# An guide for installing and configuring Antergos Linux

## Introduction

I'm going to use this README to capture the steps I took to get Antergos (re)installed successfully on my [Lenovo Thinkpad T440p](https://www.thinkwiki.org/wiki/Category:T440p).

As a novice to installing and configuring Linux, I thought I'd capture my experience of installing Antergos so that when I need to do another installation, I'll have some notes handy.

Although I'm referencing Antergos Linux specifically in this guide, my guess is that many of the steps, tools, etc. may be relevant to installing other distributions.

## Preparing for the install

1. Download Live ISO
1. Verify md5 of ISO
1. Use Bash or Etcher to create a boot-able USB from the ISO

In order to install Antergos on my Thinkpad, I first created and verified (md5) a fresh copy of the [Antergos Live ISO](https://antergos.com/download/antergos-live-iso/) on a USB flash drive.

In order to verify the ISO you downloaded before creating a Live USB, generate and compare the md5 of the ISO. Here's how to do that via a shell in Linux:

```bash
md5sum your-iso-name.iso
```

### Create Live USB

The Antergos website provides a [HOW TO for creating a Live USB](https://antergos.com/wiki/article/create-a-working-live-usb/) that I found helpful. Although it is straight forward to create the Live USB using Bash, I found using their recommended GUI for Linux called [Etcher](https://etcher.io/) a pleasure, so I'd recommend using it.

## Installation

Fortunately, there are already a lot of good articles on the installation process, so I'm not going to create yet another installation guide -- I'm just going to point out some great articles and references to checkout (along with a little commentary here and there).

* [How To Install Antergos Linux](https://itsfoss.com/install-antergos-linux/) -- this is one of the first sources I used to learn about how to perform linux installations period. Nice concise article on how to install Antergos.

* [Antergos installation guide with screenshots](https://www.ostechnix.com/antergos-installation-guide-screenshots/) -- another good step-by-step installation guide.

* [How to install Antergos 2016 in your PC](http://www.fosslinux.com/1266/how-to-install-antergos-2016-in-your-pc.htm) -- interesting installation guide that goes into more detail regarding creating partitions on your hard-drive prior to installing linux. Check out [this article](http://www.fosslinux.com/1246/20-steps-to-prepare-your-pc-for-linux-installation.htm) for more details. Note: I did NOT follow this -- I'm unsure whether it is necessary to pre-create the partitions by hand, so I ignored this advice?

* [Installing Antergos](https://antergos.com/wiki/install/installing-antergos-2/) -- the official installation page on the Antergos site.

* [ArchLinux.org Installation guide](https://wiki.archlinux.org/index.php/Installation_guide) -- the official Arch Linux installation guide. Since I'm installing Antergos, many of the items covered in this guide are not necessary/relevant for an Antergos install. However, this article contains a wealth of information regarding the installation process, so, if you run into issues this is a great reference to checkout.

## Post-install

After completing the installation of Antergos, I made a lot of changes in order to optimize the system.

### Package Management

Immediately after completing the installation, I executed an update in order to ensure that all of the packages installed were up to date before proceeding with making any changes to the OS or adding any additional software.

Immediately (more on this later), I recommend using the standard package manager called `pacman` to update the system.

Here's how to do a **system update** via pacman in the Bash shell:

```bash
# -Syu:
# S is Synchronize packages
# y is download a fresh copy of the master pkg db
# u is upgrades all packages that are out of date
sudo pacman -Syu
```

#### [pacman](https://wiki.archlinux.org/index.php/pacman)

The package management command line application that comes with Antergos.

##### Common pacman commands

* `sudo pacman -Ss` -- search for the given package
* `sudo pacman -Si` -- retrieves information for the given package
* `sudo pacman -S` -- installs the given package
* `sudo pacman -Sc` -- removes all of the cached packages from `/var/cache/pacman/pkg`
* `sudo pacman -Q` -- lists all of the installed packages
* `sudo pacman -Qs` -- retrieves information for all of the installed packages
* `sudo pacman -Qi` -- retrieves detailed information for all of the installed packages
* `sudo pacman -R` -- removes the given package; leaves behind all dependencies
* `sudo pacman -Rs` -- removes the given package and it's dependencies (not required by any other pkg)

#### [yaourt](https://archlinux.fr/yaourt-en)

yaourt is the AUR helper installed by default in Antergos, so it is a convenient method, besides using the Software Install GUI, to search for and install AUR packages.

yaourt, as a wrapper around pacman, provides the same arguments as above.

#### [pacaur](https://github.com/rmarquis/pacaur)

pacaur is another AUR helper that I installed more recently to search for and install AUR packages.

Just as yaourt is a wrapper around pacman, so too is pacaur a wrapper around pacman with additional support for AUR. So, the same rules apply -- the same arguments above will work with pacaur as they do with pacman and yaourt.

#### [pacget](https://github.com/neurobin/pacget)

pacget is a a wrapper around pacaur that provides yaourt style search results, etc.

```bash
# equivalent to sudo pacman -Syu
pacget -Syu
```

### GUI Settings

#### Settings Application

Here are specific changes I made to Gnome via the **Settings** application:

* In Privacy:
  * Turned on Location Services
  * Turned on Purge Trash & Temporary Files
* In Devices:
  * Keyboard: Added a custom Keyboard shortcut for launching a terminal (`Ctrl + Alt + T`)
  * Mouse & Touchpad: Turned off Natural Scrolling for the Touchpad
  * Displays: Adjusted external monitors Resolution (2560 x 1440); I'm running 2 4k 28" Samsung monitors
* In Details:
  * Date & Time: Adjusted Time Format to AM/PM, modified Time Zone / enabled Automatic for Date & Time, Time Zone
  * Users: Selected an image for my user

#### Tweaks Application

Here are the changes I made to Gnome via the **Tweaks** application:

* Appearance
  * Themes
    * Applications: Numix-Frost
      * Alternative: Arc-Dark\*
    * Icons: Numix-Circle\*
    * Shell: Arc-Dark\*
* Extensions
  * Cpu power manager\*\* -- control cpu profile, etc.
  * Freon\*\* -- view cpu, hdd temperatures, fan speed, etc.
  * system-monitor -- view cpu, mem, etc. stats
* Keyboard & Mouse
  * Mouse: Pointer Location on
* Top Bar
  * Battery Percentage on
  * Date on

\* = note that these themes, icons need to be installed; these are not stock.

\*\* = note that these extensions were added via the [gnome extensions website](https://extensions.gnome.org/). Follow installation/integration instructions as shown.

#### Dash to Dock Panel

Here are the changes I made to the **Dash to Dock** panel in Gnome:

* Decreased the Icon size limit to 32
* Turned off setting to use built-in theme; styled on my own
  * Shrink the dash on
  * Show windows counter indicators (yellow dot)
  * Customize the dash color (similar to original)
  * Customize opacity to 50%

### System Configuration

Here I've captured any system configuration I did to get my system to run faster, better, safer, more efficiently, etc.

#### Power Management

I'm using several tools to manage power in order to reduce heat, improve battery life, etc..

[TLP – Linux Advanced Power Management](http://linrunner.de/en/tlp/tlp.html) -- this is an important power management application to install especially for those running Linux on a laptop.

I'm not going to cover the installation and configuration of this tool -- their web site already covers it very well:

* [Installation](http://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html) -- here are the installation instructions -- see the section on Arch Linux for instructions on installing in on Antergos.

#### TL;DR

* Install the following packages: tlp, tlp-rdw
* Install these additionally if you are on a Thinkpad: acpi_call or tp_smapi
  * Note: you only need 1 of these packages -- depends upon your Thinkpad hardware.
  * I installed acpi_call as its the correct module for the Thinkpad T440p
* `sudo tlp start` -- to start the tlp service without restart (if you followed the setup correctly it should automatically start when your system starts up the next time)
* `sudo tlp-stat -s` -- to verify that tlp is working correctly
* `sudo tlp-stat` -- produce the full report

#### Antivirus

I'm using ClamAV and ClamTK (GUI) for antivirus protection on my Antergos system.

[ClamAV](https://wiki.archlinux.org/index.php/ClamAV) -- this is the official Arch Linux page that covers the basics regarding ClamAV.

I don't currently have it setup to do automatic scans yet.

Here are a few steps to keeping it up to date (definitions), etc.:

* `freshclam` -- update virus definitions via the bash shell
* `systemctl start clamd.service` -- start the service via the bash shell
* `curl https://www.eicar.org/download/eicar.com.txt | clamscan -` -- test to ensure everything is setup correctly
  * Expected output -- `stdin: Eicar-Test-Signature FOUND`
* `clamtk` -- launches the GUI for ClamAV

I've just scratched the surface here - it appears that you can include additional signatures from other repositories to broaden the number and type of signatures that ClamAV is aware of.

#### Hardware information

I've used a few different tools in order to get detailed information about things like the hard drive, memory, battery, etc..

* lshw -- command line tool that lists detailed information about the hardware of your machine.
* hardinfo -- a GUI tool that provides detailed hardware information.
* i-nex -- yet another GUI tool that provides detailed hardware information.
* hwinfo -- another hardware information command line tool

#### System information

See the Arch Linux official page on [systemd](https://wiki.archlinux.org/index.php/Systemd) for additional details.

#### [systemctl](https://wiki.archlinux.org/index.php/Systemd)

command line tool for interrogating system information (systemd)

Here are some common command line entries you can make using systemctl:

* `systemctl` -- lists all of the "units"
* `systemctl status` -- lists current status
* `systemctl --failed` -- lists any failures (units)
* `systemctl start some unit` -- start / restart / stop a unit
* `systemctl restart some unit`
* `systemctl stop some unit`
* `systemctl reboot` -- reboot the system
* `systemctl poweroff` -- power down the system

#### [journalctl](https://wiki.archlinux.org/index.php/Systemd#Journal)

systemd logging system

* `journalctl -p 3 -xb` -- lists all of the errors since the last boot

There are lots of of other \*ctl command line tools necessary for system administration.

#### Overall

[General recommendations](https://wiki.archlinux.org/index.php/General_recommendations) -- this is the "bible" from the Arch Linux site. I have to admit I've only read a few of the sections from this large repository of articles that cover a vast number of topics regarding Linux in general: System administration, Package management, Power management (especially important for a laptop), Networking, Input devices, GUI/appearance, etc.

### Display Manager

After running Antergos for a while, I noticed (after a linux update?), that the default Display Manager (DM) called [LightDM](https://wiki.archlinux.org/index.php/LightDM), was throwing nasty errors in the error log. The specific package called [lightdm-webkit2-greeter](https://aur.archlinux.org/packages/lightdm-webkit2-greeter/) was throwing errors (core dump). After reading some posts about LightDM and the webkit greeter specifically, I learned that on some systems the greeter has a tendency to misbehave. Your mileage may vary here. If you run into issues with your system's greeter you may want read further...

I performed the following diagnostic steps (from the LightDM page):

```bash
more /etc/lightdm/lightdm.conf
```

You should search the file for this title to determine what the system's current lightdm greeter is configured to use.

```bash
# lightdm.conf
[Seat:*]
...
greeter-session-lightdm-(some greeter)-greeter
```

In my case the system was configured to use the WebKit2 greeter.

I did a little research and decided to use the GTK greeter instead, in order to attempt to eliminate the errors from the logs.

Before going any further, I executed the following to see if any other greeters were installed on the system.

```bash
ls -lat /usr/share/xgreeters/

# which yielded the following:

lightdm-webkit2-greeter.desktop
```

So, I did the following to get the GTK greeter setup on my system in place of the webkit greeter.

1. Searched for and installed lightdm-gtk-greeter
1. Edited the lightdm.conf (see above) to set the gtk greeter as the default greeter.
1. Searched for and installed the lightdm-gtk-greeter-settings configuration tool.
1. Used lightdm-gtk-greeter-settings to customize the greeter.

#### lightdm-gtk-greeter-settings

I made the following configuration changes to the gtk greeter:

Appearance Tab

* Theme -- set the theme to match my current system theme (currently Adwaita Dark; see above for previously used theme details)
* Icons -- same here I set the icons to match my current system icons (currently Numix-Circle)
* Background Image -- I found and selected one of the Antergos background images from the `/usr/share/antergos/wallpapers/` folder.

Panel Tab

* Clock format -- set the format to one that is similar to my desktop format. `%a %b %d, %I:%M %p` => "Sun Jan 28, 05:27 PM"

### Software

Here is a list of all of the software packages, from system tools to audio and video applications, that I've installed on Antergos.

#### Applications

Here, in no particular order, are the applications that I have installed.

* **Atom** -- great all purpose text editor
* **Visual Studio Code** -- great JavaScript editor/all purpose text editor
  * As a tweak to Code, I've installed `Fira Code` and enabled font ligatures in user settings
  * As a developer who uses Windows by day, and MacOS and Linux at home, it's nice to have a cross platform editor that more or less behaves the same across all three environments.
* **BleachBit** -- tool for securely removing files, freeing up disk space, etc.
* **Chromium** -- open source browser from Google
* **Chrome** -- closed source version of Chromium from Google
* **Evolution** -- great email client
  * **evolution-esw** -- used to connect Evolution to Office365/Exchange email servers
  * Also made use of Online Accounts section in Gnome to setup Office365 account once evolution-ews was installed
* **ClamAV** -- good antivirus command line tool
* **ClamTK** -- good GUI for ClamAV antivirus tool
* **Etcher** -- great USB creation tool; great for burning a Live ISO to a USB flash drive
* **Franz** -- interesting application for accessing several social media accounts via a single GUI
* **FSearch** -- GUI file system search tool
* **GParted** -- Graphical partitioning tool
* **GVim** -- great GUI version of the venerable `vim` available in the Bash shell
* **I-Nex** -- a GUI tool that provides detailed hardware information
* **JetBrains Toolbox** -- GUI utility for downloading JetBrains products, e.g. Intellij, Web Storm, etc.
* **LibreOffice** -- strong, open source MS Office style suite of productivity software
* **MegaSync** -- Dropbox like cloud storage service available via a GUI
* **Meld** -- great diff and merge GUI tool; I use this with git as my `difftool` and `mergetool`
* **Opera** -- open source browser from Opera
* **Pomodoro** -- Pomodoro timer -- Gnome compatible
* **PSensors** -- similar to XSensors, a GUI for viewing the current temperatures of various components in the system
* **Simplenote** -- Open source note taking application ala Evernote
  * NOTE: I couldn't find an open source application that integrated with Evernote
* **SmartGit** -- great cross platform git GUI
* **Spotify** -- great streaming music GUI
* **Sublime Text 3** -- great all purpose text editor
* **Stacer** -- nice GUI utility for examining overall system performance
* **Vivaldi** -- open source browser by the form CEO of Opera
* **VLC** -- great media player
* **Web Storm** -- installed via the JetBrains Toolbox (above) - a JavaScript IDE (NOTE: not open source - trial only)
* **Xmind** -- nice mind mapping application
* **XSensors** -- nice GUI for viewing the current temperatures of the core and CPU
* **ZenMap** -- GUI for nmap port mapping utility

#### Tools

These "tools", much like the applications above, are ones that I've installed. I'm loosely defining "tools" to be applications that are primarily or solely accessed via the command line (Bash) and typically used for system administration-type tasks -- power management, bluetooth management, etc.

* **blueman** -- good, additional bluetooth device management GUI
* **brightness-controller** -- great little utility GUI for controlling your monitors' brightness
* **dotnet-sdk** -- .net core 2.0 libraries for writing .net core apps on linux
  * This will install dependencies: dotnet-host, dotnet-runtime
* **evolution-ews** -- Exchange Web Services for accessing exchange / Office 365 servers from Evolution
* **fing** -- network scanner
* **fish** -- colorized, auto-suggesting, etc. shell; nice to use in addition to Bash
  * In addition to fish, installing oh my fish (OMF) allows you to install themes, etc.
  * I've installed the `shellder` theme that is ideal for GIT
* **git** -- source control command line tools
* **hardinfo** -- a GUI tool that provides detailed hardware information
* **hwinfo** -- another hardware information command line tool
* **JDK 8** -- ?? not sure but something on the system required this be installed ...??
* **LightDM-GTK-Settings** -- GUI configuration tool for the LightDM GTK3
* **linux-api-headers** -- dependency?
* **lm_sensors** -- monitoring library - provides access to things like CPU temp, fan speeds, etc.
* **lshw** -- command line tool that lists detailed information about the hardware of your machine.
* **nodejs** -- stand alone JavaScript engine
* **npm** -- node package manager - companion command line tool for managing node packages
* **tlp** -- power management for linux; helps optimize battery life, facilitates reporting on some hardware statistics
* **iw** -- command line based wireless device configuration utility; used / installed at the same time as tlp
* **smartmontools** -- used by tlp to emit SMART hard drive statistics(?)
* **thermald** -- linux thermal daemon (Intel CPUs)
* **xbacklight** -- command line utility for adjusting the back light (brightness) of your monitors
* **x86_Energy_Perf_Policy** -- ?
* **pacaur** -- AUR Helper
* **pacget** -- wrapper around pacaur; yaourt styled results
* **Fira Code** -- nice font for programming -- allows ligatures
* **Albert-Lite** -- great launcher ala spotlight in macOS; light version doesn't have as many funky dependencies
* **INXI** -- utility for reviewing system properties; provides suggestions

#### Themes & Icons

I installed the following icons and wallpapers in order to jazz up my desktop a bit.

* **numix-icon-theme-circle**
* **antergos-wallpapers-deepin**
* **antergos-wallpapers-extra**
