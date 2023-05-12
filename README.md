# borg-offsite-backup: help back up Qubes VMs and ZFS file systems

Sample configuration `/etc/borg-offsite-backup.conf`:

```
{
    "myself": "dom0",
    "backup_server": "milena.dragonfear",
    "backup_user": "qubes_backup_dom0",
    "bridge_vm": "backup",
    "ssh_from": "user"
    "datasets_to_backup": [
        "tank/ROOT/os",
        "tank/home",
        "tank/varlibqubes",
        {"name": "tank/qubes/*/private", "glob": true},
        {"name": "tank/qubes/*-tpl/root", "glob": true}
    ],
    "exclude_patterns": [
        "var/lib/qubes/*/*/root-cow.img.*",
        "var/lib/qubes/*/*/private-cow.img.*",
        "var/lib/qubes/*/*/volatile.img",
        "var/lib/qubes/appvms/disp*",
        "*/.cache",
        "*/*/.cache",
        "var/cache/*/*",
        "*/.config/borg",
        "var/lib/systemd/coredump",
        "*/.Trash-*",
        "*/*/.Trash-*",
        "var/tmp/*",
        "tmp/*"
    ],
    "filesystems_to_backup": [
        "/boot",
        "/boot/efi"
    ],
}
```

The Borg key will by default be stored in `~/.borg-offsite-backup.key`.
