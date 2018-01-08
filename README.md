# An guide for installing and configuring Antergos Linux

## Introduction

I'm going to use this README to capture the steps I took to get Antergos (re)installed successfully on my [Lenovo Thinkpad T440p](https://www.thinkwiki.org/wiki/Category:T440p).

As a novice to installing and configuring Linux, I thought I'd capture my experience of installing Antergos so that when I need to do another installation, I'll have some notes handy.

Although I'm referencing Antergos Linux specifically in this guide, my guess is that many of the steps, tools, etc. may be relevant to installing other distros.

## Preparing for the install

1. Download Live ISO
2. Verify md5 of ISO
3. Use Bash or Etcher to create a bootable USB from the ISO

In order to install Antergos on my Thinkpad, I first created and verified (md5) a fresh copy of the [Antergos Live ISO](https://antergos.com/download/antergos-live-iso/) on a USB flash drive.

In order to verify the ISO you downloaded before creating a Live USB, generate and compare the md5 of the ISO.  Here's how to do that via a shell in Linx:

```

md5sum your-iso-name.iso

```

### Create Live USB
The Antergos website provides a [HOW TO for creating a Live USB](https://antergos.com/wiki/article/create-a-working-live-usb/) that I found helpful.  Although it is straight forward to create the Live USB using Bash, I found using their recommended GUI for Linux called [Etcher](https://etcher.io/) a pleasure, so I'd recommend using it.

## Installation

Fortunately, there are already a lot of good articles on the installation process, so I'm not going to create yet another installation guide -- I'm just going to point out some great articles and references to checkout (along with a little commentary here and there).

* [How To Install Antergos Linx](https://itsfoss.com/install-antergos-linux/) -- this is one of the first sources I used to learn about how to perform linux installations period.  Nice concise article on how to install Antergos.

* [Antergos installation guide with screenshots](https://www.ostechnix.com/antergos-installation-guide-screenshots/) -- another good step-by-step installation guide.

* [How to install Antergos 2016 in your PC](http://www.fosslinux.com/1266/how-to-install-antergos-2016-in-your-pc.htm) -- interesting installation guide that goes into more detail regarding creating partitions on your harddrive prior to installing linux.  Check out [this article](http://www.fosslinux.com/1246/20-steps-to-prepare-your-pc-for-linux-installation.htm) for more details.  Note:  I did NOT follow this -- I'm unsure whether it is necessary to pre-create the partitions by hand, so I ignored this advice?

* [Installing Antergos](https://antergos.com/wiki/install/installing-antergos-2/) -- the official installation page on the Antergos site.

* [ArchLinux.org Installation guide](https://wiki.archlinux.org/index.php/Installation_guide) -- the official Arch Linux installation guide.  Since I'm installing Antergos, many of the items covered in this guide are not necessary/relevant for an Antergos install.  However, this article contains a wealth of information regarding the installation process, so, if you run into issues this is a great reference to checkout.

## Post-install

After completing the installation of Antergos, I made a lot of changes in order to optimize the system.

### Package Management

Immediately after completing the installation, I executed an update in order to ensure that all of the packages installed were up to date before proceeding with making any changes to the OS or adding any additional software.

Immediately (more on this later), I recommend using the standard package manager called ```pacman``` to update the system.

Here's how to do a **system update** via pacman in the Bash shell:

```Bash
# -Syu:
# S is Synchronize packages
# y is download a fresh copy of the master pkg db
# u is upgrades all pkgs that are out of date
sudo pacman -Syu

```

#### pacman

##### Common pacman commands:

* ```sudo pacman -Ss``` -- search for the given package
* ```sudo pacman -Si``` -- retrieves information for the given package
* ```sudo pacman -S``` -- installs the given package
* ```sudo pacman -Sc``` -- removes all of the cached packages  from ```/var/cache/pacman/pkg```
*

* ```sudo pacman -Q``` -- lists all of the installed packages
* ```sudo pacman -Qs``` -- retrieves information for all of the installed packages
* ```sudo pacman -Qi``` -- retrieves detailed information for all of the installed packages


* ```sudo pacman -R``` -- removes the given package; leaves behind all dependencies
* ```sudo pacman -Rs``` -- removes the given package and it's dependencies (not required by any other pkg)

#### yaourt



#### pacaur




#### Here are some great package management (including AUR) references:

* [Pacman](https://wiki.archlinux.org/index.php/pacman) -- this is the official Arch Linux page on Pacman.


### Antergos Settings



### Software




* [ArchLinux.org General recommendations](https://wiki.archlinux.org/index.php/General_recommendations) -- this is the "bible" from the Arch Linux site.  I have to admit I've only read a few of the sections from this large repository of articles that cover a vast number of topics regarding Linux in general:  System administration, Package management, Power management (especially important for a laptop), Networking, Input devices, GUI/apearance, etc.
