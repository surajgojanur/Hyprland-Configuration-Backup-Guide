# Hyprland Configuration Backup Guide

This repository provides a **step-by-step guide** and a **backup script** for safely backing up your Hyprland configuration on Fedora (or any Linux distro with Hyprland).

---

## Why Back Up?

Hyprland stores your configuration in plain text files (`~/.config/hypr/hyprland.conf`). Experimenting with keybinds, layouts, or other settings may break your setup. A backup ensures you can **restore your working setup instantly**.

---

## Backup Locations

- **Primary config file**: `~/.config/hypr/hyprland.conf`  
- **Optional extra files/folders**: `~/.config/hypr/conf.d/`

---

## Manual Backup

### 1. Single-file backup
```bash
cp ~/.config/hypr/hyprland.conf ~/.config/hypr/hyprland.conf.bak
