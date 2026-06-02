# CLI Reference

Use the CLI when possible. It handles OAuth PKCE, local callback handling, token storage, automatic access-token refresh, bearer authentication, JSON input, and response export.

## Install first

```bash
npm install -g @interactorai/agent-cli
interactor-agent --help
```

If the environment has a package-manager policy, follow that policy.

Verification steps:

- Check if the CLI is already installed.
- If not, install it.
- If you encountered an issue during installation, ensure you configure your environment correctly and try again.
- Only if installation didn't work: read `references/raw-api.md`.

## Install This Skill

Install the Interactor skill from GitHub into a local skills root:

```bash
interactor-agent skills install <skills-root-path>
```

The command installs the skill into `<skills-root-path>/interactor`. Use `--force` only when you want to replace an existing local copy.

## Authentication

Login:

```bash
interactor-agent auth login --client-id <agent-or-tool-identifier>
```

The CLI prints the owner approval URL. If Enter is pressed in an interactive terminal, it opens the URL in the browser. The owner signs in and approves access in the browser.

Useful auth commands:

```bash
interactor-agent auth status
interactor-agent auth refresh
interactor-agent auth logout
```

The CLI refreshes stale access tokens before protected requests automatically. If refresh fails, run login again.

## Schemas

Schema commands:

```bash
interactor-agent schemas full
interactor-agent schemas patch
```

The schema responses include field purpose, allowed enum-like values, and read-only metadata.

## List And Inspect

```bash
interactor-agent interactors list
interactor-agent interactors get <interactor-id>
```

The list response includes each Interactor's id, name, type, state, timestamps, public URL, and owner URL.

## Create

Create from a file:

```bash
interactor-agent interactors create --file ./interactor.json
```

Create from stdin:

```bash
interactor-agent interactors create --stdin < ./interactor.json
```

Create from inline data only for small payloads:

```bash
interactor-agent interactors create --data '{"name":"Example","type":"service","modules":{}}'
```

After creation, the response includes the created Interactor. Use `interactors get` if you need a fresh read.

## Patch

Patch from a file:

```bash
interactor-agent interactors patch <interactor-id> --file ./patch.json
```

Patch from stdin:

```bash
interactor-agent interactors patch <interactor-id> --stdin < ./patch.json
```

Before preparing a patch body, read `references/patching-behavior.md`.

Read-only values are ignored.

## Output Files

Most commands support:

```bash
--output ./response.json
--quiet
```

Use output files when another step needs the response.

## Local Images

For images already available by URL, set the relevant image URL field directly when the schema supports it.

For local image files include url with the base64 image encoded. If you need to upload many images at once, split them across several patches.

Common image fields include avatar, chat header image, product images, service images, welcome message media, and team member photos.
