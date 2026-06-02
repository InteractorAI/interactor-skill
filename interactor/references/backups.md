# Keeping Backups

- Interactor does not provide a versioning system. If you need backups, do it yourself.
- To restore a backup, patch the Interactor with the old version.
- Backup payloads must omit ids. The entities can be removed by the time you restore it.
- If you need to back up an image, download it. Interactor-hosted images are deleted when not used in an Interactor.
