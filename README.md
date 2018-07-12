# Simply Linux

![screenshot](https://pre00.deviantart.net/96d5/th/pre/f/2010/175/b/6/dwm__float__by_edma2.png)

Install Linux *the hard way*. For those who love minimalism, simplicity and mindfulness of what's going on under the hood. Congnitive load is higher than usual! So don't try to do it *one* day/week/month. Be patient, calm and detached. If it burdens you - f\*ck it!

## Stack
These tools are chosen carefully and wisely.

[base]
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

[toolbox]
* openntpd - to set system time from internet 

## Legend
* `[--flag]` - optional flag. Shown to be clear what's implied.

## Create Live USB
### Get USB stick and plug it

*(!) all data will be destroyed*

Linux
```bash
# mount
sudo mount /dev/sdx /mnt
# go https://repo.voidlinux.eu/live/current/ and get the latest Void Linux
cd ~/Downloads
sudo dd bs=4M if=void-live-x86_64-20171007.iso of=/dev/sdx && sync
```

Windows
```
Get uniboot
```

### Reboot and boot from the media

Now you're in
```bash
...

voidlinux login: |
# login root
# password voidlinux
```

Set correct system & hardware time
```bash
# show Hardware Clock
hwclock [--show] # if `Cannot access the Hardware Clock via ..` hwclock --directisa
# show System Clock
date
# compare
# a. if the only system is correct
hwclock --systohc
# b. if only hardware is correct
hwclock --hctosys
# c. if you want to set hardware clock manually
hwclock --set [--utc] --date='16:25' # or --date='2020-08-05 16:25:59'
#    repeat b.
# d. if you want to set system clock manually
date --date='16:25' # or --date='2020-08-05 16:25:59'
#    repeat a.
# e. if you want to set system clock from internet
xbps-install openntpd
ln -s /etc/sv/openntpd /var/service/
#    done; now ntpd daemon is running; repeat a.
```

### Prepare package manager
TODO
```
prepare package manager
vi /etc/xbps.d/timfayz.conf >> “repository=http://…”
xbps-install -Su
```

#### ...
