# Patching Behavior Reference

Patch bodies are partial semantic Interactor objects. Omitted object fields remain unchanged. Object fields merge into the current semantic state.

Arrays are replacement/upsert surfaces:

- Include the full desired array whenever you touch an array.
- Include ids to edit or retain existing items.
- Omit ids only to create new items.
- Omit existing items from the array only when you intend to delete them.

For a one-item edit inside an array, first read the current Interactor, copy the full current array into the patch, preserve every retained item's id, change only the target item, and then patch. Never send only the changed array item unless deleting every other item is intended and approved.

If an array item was already deleted by an earlier patch, do not restore it with its old id. Read the current Interactor again and recreate missing items without ids, while preserving ids for items that still exist.
