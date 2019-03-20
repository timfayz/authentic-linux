# Authentic Linux 🌱 

![screenshot](authentic-linux.jpg)

Want to install Linux *the hard way*? Love minimalism, simplicity and awareness of what's going on under the hood? Authentic Linux is what you need! :] Be careful, cognitive load is higher than usual! So don't try to do it *one* day/week/month. Be patient, calm and detached. If it burdens you - just throw it for several days!

## Intro
Authentic Linux is a set of instructions how to manually install and configure minimal Linux distribution without any Wizards and much of pre-installed weight. Through the steps you will acquire a firm understanding how different packages, config files, bootloaders and many other stuff tied together. The instructions are based on many well-known resources and personal experience. It includes IBM developerWorks, Arch, Alpine and Void Wikis. I tried to find a "Golden ration" between awareness of what you do, visual aesthetics, comfortable user experience on daily basis and amount of manual work. You will not find anything building from sources unless there is *no way* but do it! So we will stick to configure packages out of the box when possible. 

## Message to Newbies
This manual is a message back to myself in the past. Don't try to know & do *everything*! Especially when it comes to Linux! Believe me, one day you will just remain a depressed nerd surrounded by burdensome thoughts. Anyway, at the end, no one knows what's actually going on under the hood (even Linus T. itself). Since the time of Alan Turing and punch cards are gone - no one capable to do that at the current scale. Thus, always keep in mind - *no one* can know *everything*; only some pieces either wide or narrow. It's much better to know *enough* in order to ask a *right question* in the *right place*.

## Features
* Low memory footprint (~55mb)
* Visually consistent (one color & font scheme)
* Backed by the most supported packages

## Package stack
This is the list of packages we will stick with in order to build our dream, hackable and cool-looking Linux:

**Base**
* Syslinux - as bootloader to load any Linux distribution
* Void Linux - as a base Linux distribution and its `xbps` package manager
* bash - as a default shell
* Xorg - as a default display server and GUI mode

**CLI mode**
* tmux - as a terminal multiplexer to preserve sessions
* neovim - as a default CLI text-editor
* irssi - as an IRC client
* slstatus - status bar to print system info (CPU load, time, etc)
* openntpd - synchronize system time from internet
* GNU toolchain - gpg, openssh, iconv, etc

**X/GUI mode**
* dwm - as tiling window manager (WM)
* st - as terminal emulator
* vscode - as full-fledged IDE
* firefox - as a Web browser
* viewnior - image viewier
* feh - background image setter
* imagemagick - to make screenshots, convert images, etc
* krita - simple image editor

## Unified color experience
Through the evolution of different IDEs and code editors there are several themes trying to unify visual experience across different platforms and applications. One of them (in the field of CLI and TUI) is [base16](https://github.com/chriskempson/base16). I find it very distinguishable, crisp and natural. Other ones are [Dracula](https://draculatheme.com/) and [Solarized](https://ethanschoonover.com/solarized/). Color theme is a matter of preference. Ss for me, the most important aspect was *consistence* across the apps. Also, I don't like palette and transitional colors (neither blue or black but opaque mix of them). I prefer either "dark" theme with quite good contrast or "light" one, where background would be obviously white. 

As for Authentic Linux I stick with simple dark & white color theme. But don't worry! Going along the way you will understand how to fit aesthetics to your taste!

---
## Let's get started!
Enough working with tongue! It's time to make something by hands!

A quick legend used through the code blocks:

* `[--flag]` - optional flag. Shown to be clear what *is* implied.

### Create Live USB

#### 1. Get your USB-stick and plug it

*(!) Attention! All data will be destroyed!*

**Linux**
```bash
# mount
sudo mount /dev/sdx /mnt
# go https://repo.voidlinux.eu/live/current/ and get the latest Void Linux
cd ~/Downloads
sudo dd bs=4M if=void-live-x86_64-xxx.iso of=/dev/sdx && sync
```

**Windows**
```
- Get uniboot
- Burn void-live-x86_64-xxx.iso into the USB-stick
```

#### 2. Reboot and boot from the media

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
#    repeat b; done.
# d. if you want to set system clock manually
date --date='16:25' # or --date='2020-08-05 16:25:59'
#    repeat a; done.
# e. if you want to set system clock from internet
xbps-install openntpd
ln -s /etc/sv/openntpd /var/service/
#    now ntpd daemon is running; repeat a; done.
```

#### 3. Prepare package manager
```
prepare package manager
vi /etc/xbps.d/timfayz.conf >> “repository=http://…”
xbps-install -Su
```

#### 4. Color experience across the apps
* Expain how to setup base16 for nvim, st, code

#### 5. Set, test and capture VT/Terminal color scheme
* Use https://github.com/EvanPurkhiser/linux-vt-setcolors <br>
(set VT colorscheme)
* https://github.com/chriskempson/base16-shell
(show VT colorscheme)
* https://bisqwit.iki.fi/source/snapscreenshot.html <br>
(take VT screenshots) `./configure && make install`

#### 6. Font experience across the apps
Explain how to setup fonts in VT, X11 in general and other apps.

* Download Terminus font https://files.ax86.net/terminus-ttf/#download
* `sudo fc-cache`
* `vi ~/.config/fontconfig/fonts.conf` -> "Terminus (TTF)"

#### 7. Keep user preference in tact
Explain how to backup everything into `dotfiles`
