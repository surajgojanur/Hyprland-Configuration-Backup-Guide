## 1️⃣ Clone the Repository

Copy the repository to your local machine:

```bash
# SSH
git clone git@github.com:YOUR_USERNAME/HyprlandBackupGuide.git

# OR HTTPS
git clone https://github.com/YOUR_USERNAME/HyprlandBackupGuide.git
````

After cloning:

```bash
cd HyprlandBackupGuide
```

Your repo folder should now contain:

* `README.md` – this guide
* `backup.sh` – automated backup script
* (optional) `.gitignore`

---

## 2️⃣ Inspect the Repository

Check files inside:

```bash
ls -l
```

Expected output:

```
-rwxr-xr-x 1 user user  800 Sep 27 16:50 backup.sh
-rw-r--r-- 1 user user  900 Sep 27 16:50 README.md
```

Make sure `backup.sh` is executable:

```bash
chmod +x backup.sh
```

---

## 3️⃣ Automated Backup

Run the script:

```bash
./backup.sh
```

What it does:

1. Creates a backup folder `~/HyprlandBackup` if it doesn’t exist
2. Copies your main config `hyprland.conf` with a timestamp
3. Copies the entire `~/.config/hypr` folder into a timestamped folder

Example output:

```
Backup created: /home/god/HyprlandBackup/hyprland.conf.2025-09-27-1705.bak
Full folder backup created: /home/god/HyprlandBackup/hypr_config_backup_2025-09-27-1705
Backup complete ✅
```

Verify backups:

```bash
ls ~/HyprlandBackup
```

---

## 4️⃣ Manual Backup (Optional)

```bash
# Single file backup
cp ~/.config/hypr/hyprland.conf ~/.config/hypr/hyprland.conf.bak

# Timestamped backup
cp ~/.config/hypr/hyprland.conf ~/.config/hypr/hyprland.conf.$(date +%Y-%m-%d-%H%M).bak

# Entire folder backup
cp -r ~/.config/hypr ~/HyprlandBackup
```

---

## 5️⃣ Restoring a Backup

### Step 1: Find your backup

```bash
ls ~/HyprlandBackup
```

Example result:

```
hyprland.conf.2025-09-27-1705.bak
hypr_config_backup_2025-09-27-1705
```

### Step 2: Restore single file

```bash
cp ~/HyprlandBackup/hyprland.conf.2025-09-27-1705.bak ~/.config/hypr/hyprland.conf
```

### Step 3: Restore entire folder

⚠️ This will overwrite your current Hyprland folder.

```bash
rm -rf ~/.config/hypr
cp -r ~/HyprlandBackup/hypr_config_backup_2025-09-27-1705 ~/.config/hypr
```

### Step 4: Reload Hyprland

```bash
hyprctl reload
```

Your restored configuration is now active.

---

## 6️⃣ Using Git to Track Changes

Optional but recommended:

```bash
git add .
git commit -m "Backup and usage guide"
git push
```

* Commit any changes to `backup.sh` or your configuration guide
* Track changes and roll back if needed

---

## 7️⃣ Advanced Tips

* Use **tab-completion** to avoid typing long filenames
* Keep multiple backups — the script automatically timestamps them
* You can schedule automatic backups using `cron` or `systemd timers`

Example cron entry to backup every day at 10 PM:

```cron
0 22 * * * /home/god/HyprlandBackupGuide/backup.sh
```

* Store backups on a separate drive or cloud for extra safety

---

## 8️⃣ Quick Commands Cheat Sheet

| Task                       | Command                                                                                         |
| -------------------------- | ----------------------------------------------------------------------------------------------- |
| Run automated backup       | `./backup.sh`                                                                                   |
| List backups               | `ls ~/HyprlandBackup`                                                                           |
| Restore latest file backup | `cp ~/HyprlandBackup/hyprland.conf.<TAB> ~/.config/hypr/hyprland.conf`                          |
| Restore entire folder      | `rm -rf ~/.config/hypr && cp -r ~/HyprlandBackup/hypr_config_backup_<TIMESTAMP> ~/.config/hypr` |
| Reload Hyprland            | `hyprctl reload`                                                                                |

---
