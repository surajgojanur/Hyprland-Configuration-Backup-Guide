
---

# 2️⃣ `backup.sh` script

Create a file `backup.sh` in the repo with:

```bash
#!/bin/bash

# Hyprland backup script
# Author: Your Name
# Usage: ./backup.sh

CONFIG_DIR="$HOME/.config/hypr"
BACKUP_DIR="$HOME/HyprlandBackup"

# Create backup folder if not exists
mkdir -p "$BACKUP_DIR"

# Timestamp
TIMESTAMP=$(date +%Y-%m-%d-%H%M)

# Backup main config file
if [ -f "$CONFIG_DIR/hyprland.conf" ]; then
    cp "$CONFIG_DIR/hyprland.conf" "$BACKUP_DIR/hyprland.conf.$TIMESTAMP.bak"
    echo "Backup created: $BACKUP_DIR/hyprland.conf.$TIMESTAMP.bak"
else
    echo "No hyprland.conf found in $CONFIG_DIR"
fi

# Backup entire folder
cp -r "$CONFIG_DIR" "$BACKUP_DIR/hypr_config_backup_$TIMESTAMP"
echo "Full folder backup created: $BACKUP_DIR/hypr_config_backup_$TIMESTAMP"

echo "Backup complete ✅"
