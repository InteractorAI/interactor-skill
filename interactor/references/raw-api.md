# Raw API Reference

Use raw endpoints when the CLI is unavailable, when building a hosted integration, or when the agent runtime must manage OAuth itself.

Environment domains:

- Website: `https://interactor.ai/`
- API: `https://api.interactor.ai`

## OAuth PKCE Flow

Interactor exposes OAuth authorization-code flow with PKCE.

1. Load OAuth discovery metadata.
2. Generate `state`, `code_verifier`, and S256 `code_challenge`.
3. Start a redirect listener before sending the owner to the authorization URL.
4. Send the owner to the authorization endpoint in a browser.
5. Verify returned `state`.
6. Exchange `code` for tokens.
7. Store tokens securely.
8. Refresh access tokens when stale.

Do not collect passwords, cookies, authorization codes, access tokens, or refresh tokens from the owner manually.

### Discovery

```http
GET https://api.interactor.ai/.well-known/oauth-authorization-server
```

Important fields:

- `authorization_endpoint`
- `token_endpoint`
- `revocation_endpoint`
- `response_types_supported`
- `grant_types_supported`
- `code_challenge_methods_supported`
- `token_endpoint_auth_methods_supported`

### Authorization Request

Open the owner approval URL in a browser:

```text
<authorization_endpoint>?response_type=code&client_id=<client-id>&redirect_uri=<redirect-uri>&state=<state>&code_challenge=<challenge>&code_challenge_method=S256
```

Requirements:

- Use `response_type=code`.
- Use a stable `client_id` that identifies the requesting agent or tool.
- Use a redirect URI without a URL fragment.
- Verify the returned `state`.
- Use `code_challenge_method=S256`.
- Keep the `code_verifier` private until token exchange.

Hosted agents should use HTTPS redirect URLs. Local agents can use a loopback redirect:

```text
http://127.0.0.1:<port>/callback
```

### Token Exchange

```http
POST https://api.interactor.ai/oauth/token
Content-Type: application/x-www-form-urlencoded

grant_type=authorization_code
client_id=<client-id>
redirect_uri=<same-redirect-uri>
code=<authorization-code>
code_verifier=<code-verifier>
```

### Refresh

```http
POST https://api.interactor.ai/oauth/token
Content-Type: application/x-www-form-urlencoded

grant_type=refresh_token
client_id=<client-id>
refresh_token=<refresh-token>
```

If refresh fails, start a new OAuth flow. Do not repeatedly retry a rejected refresh token.

### Revoke

```http
POST https://api.interactor.ai/oauth/revoke
Content-Type: application/x-www-form-urlencoded

token=<access-or-refresh-token>
client_id=<client-id>
```

## Agent Management Endpoints

Protected requests use:

```http
Authorization: Bearer <access-token>
```

### Schemas

```http
GET https://api.interactor.ai/api/agent/v1/schemas/interactor-full
GET https://api.interactor.ai/api/agent/v1/schemas/interactor-patch
```

The schema responses include field purpose, allowed enum-like values, and read-only metadata.

### List Interactors

```http
GET https://api.interactor.ai/api/agent/v1/interactors
```

Expected response shape:

```json
{
  "interactors": [
    {
      "id": 123,
      "name": "Example",
      "type": "service",
      "state": "active",
      "publicUrl": "https://interactor.ai/example/",
      "ownerUrl": "https://interactor.ai/interactors/123",
      "createdAt": "2026-01-01T00:00:00.000Z",
      "updatedAt": "2026-01-01T00:00:00.000Z"
    }
  ]
}
```

### Get Interactor

```http
GET https://api.interactor.ai/api/agent/v1/interactors/<interactor-id>
```

The response includes the semantic Interactor payload and ids needed for precise edits.

### Create Interactor

```http
POST https://api.interactor.ai/api/agent/v1/interactors
Content-Type: application/json
Authorization: Bearer <access-token>

<semantic-interactor-create-payload>
```

Create payloads use the semantic Interactor shape accepted by the full schema. Do not include read-only fields.

### Patch Interactor

```http
PATCH https://api.interactor.ai/api/agent/v1/interactors/<interactor-id>
Content-Type: application/json
Authorization: Bearer <access-token>

<semantic-interactor-patch-payload>
```

Omitted fields remain unchanged. Arrays replace/upsert their corresponding lists; preserve ids for existing items that should be edited or retained.

## Safe API Behavior

- Store tokens using the host platform's secret storage.
- Redact tokens and authorization codes from logs.
- Treat 401 as a signal to refresh once, then re-authenticate if needed.
- Treat 403 as "this owner cannot access that Interactor."
- Read back after mutations before reporting success.
