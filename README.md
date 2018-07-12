# Element Linux

![screenshot](https://pre00.deviantart.net/96d5/th/pre/f/2010/175/b/6/dwm__float__by_edma2.png)

Install Linux *the hard way*. For those who love minimalism, simplicity and mindfulness of what's going on under the hood.

## Stack
* Syslinux - as bootloader for any Linux distribution
* Void Linux - as a base distribution and package manager
* Xorg - as display server
* dwm - as tiling window manager (WM)
* slstatus - status bar to print system info in both tmux/DWM (CPU load, time, etc)
* st - as terminal emulator
* tmux - as terminal multiplexer (regardless of GUI/console mode)
* vis - as main text-editor
* vscode - as IDE
* firefox - as a browser

## Prepare
1. Get USB stick and plug (data will be destroyed!). Run your system (I assume we've some already installed system)
**If Linux:**
```bash
# mount
sudo mount /dev/sdx /mnt
# go https://repo.voidlinux.eu/live/current/ and get the latest Void Linux
cd ~/Downloads
sudo dd bs=4M if=void-live-x86_64-20171007.iso  of=/dev/sdx && sync
```
**If Windows**
```
```

#### Reboot and boot from the media

```

```

```
code
```
