# Module Item Resources

Use item resources for changes to one item in a list-based module. This is the
recommended editing path because it avoids resending unrelated items and reduces
the chance of overwriting concurrent changes.

## Version check

```bash
interactor-agent --version
```

- CLI 0.1.0 or newer: use `interactors modules <module> items`.
- CLI 0.0.x: upgrade if possible. If upgrading is currently impossible, use the
  fallback under **Older CLI fallback**.

## Supported modules

| Module name | Item | Reorder |
| --- | --- | --- |
| `knowledge` | knowledge section | no |
| `services` | service | yes |
| `team` | team member | yes |
| `faq` | FAQ item | yes |
| `forms` | custom form | no |
| `greeting` | greeting message | yes |
| `shortcutsMenu` | shortcut menu item | yes |
| `products` | product | yes |
| `scheduler` | supported appointment type | yes |
| `smartLinks` | smart link | no |
| `alerts` | alert task | yes |

## Safe workflow

1. List the current module items and use ids exactly as returned.
2. Load the module's exact item schemas before preparing input:

   ```bash
   interactor-agent interactors modules <module-name> items schema
   ```

   The response includes `createSchema`, `patchSchema`, and whether the module
   supports reordering.
3. Choose exactly one operation: create, update, delete, or reorder.
4. Read the module items again after the mutation and verify the result.

Create one item:

```bash
interactor-agent interactors modules <module-name> items create <interactor-id> \
  --file ./item.json
```

Create bodies contain the new item fields and no id.

Partially update one item:

```bash
interactor-agent interactors modules <module-name> items update <interactor-id> \
  --item-id '<item-id>' \
  --file ./item-patch.json
```

Send only changed fields. Nested objects are partial where supported. For custom
forms, `schema` is JSON and is replaced as a complete field. If validation
fails, use the detailed validator error and inspect the module's item schema
before retrying.

Delete one item:

```bash
interactor-agent interactors modules <module-name> items delete <interactor-id> \
  --item-id '<item-id>'
```

Delete only after confirming when the item contains meaningful owner content.

Reorder items:

```bash
interactor-agent interactors modules <module-name> items reorder <interactor-id> \
  --data '{"ids":["ItemType:2","ItemType:1"]}'
```

The ids array is the complete desired order and must contain every current item
id exactly once. Reorder is unavailable for modules marked `no` in the table.

## Root full import or replacement

The root command remains supported:

```bash
interactor-agent interactors patch <interactor-id> --file ./patch.json
```

Use it for module settings or when a full import/replace is intentional. Root
list fields still use the older replacement/upsert behavior: send the complete
desired list, preserve ids for retained items, omit ids for new items, and omit
stored items only when deletion is intended. Read `references/patching-behavior.md`.

## Older CLI fallback

If CLI 0.1.0 or newer cannot be installed, CLI 0.0.x can still use the root API:

1. Run `interactor-agent interactors get <interactor-id>` immediately before the
   change.
2. Copy the complete current list into a root patch.
3. Preserve every retained item id.
4. Apply the create, edit, delete, or reorder in that complete list.
5. Run `interactor-agent interactors patch <interactor-id> --file ./patch.json`.
6. Read the Interactor again and verify that unrelated items were preserved.

Do not send only one array item through the root patch API; doing so can remove
the other stored items.
