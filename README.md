# Bootable Gentoo Image for Raspberry Pi 1 and zero

On a Rpi 1 B+ with a whoping 256MB of RAM, configured as 128/128 split between
GPU and CPU:
![shell screenshot][1]

Bootable image with minimal system and some dev tools. The main purpose of this
build is to serve as a base system for [SoFIS][2]. However it can be used for
virtually anything.

Profile: default/linux/arm/17.0/armv6j\
Kernel+modules: Raspbian 5.4.83+

## How to use

This project provides bootable SD Card image, based on a 8GB card. This means
that your SD Card must be at least (can be bigger) 8GB for this image be written
as-is. The image provides the following partitions:

| Partition | Size   | Content                 |
|-----------|--------|-------------------------|
| 1         | 268 MB | Boot, from Raspbian     |
| 2         | 6.9 GB | Gentoo system           |
| 3         | 696 MB | Swap                    |

*WARNING* The following instructions *can* break your system if done improperly.
Be sure of the device you are writting to: A mistake here means a wiped hard
drive. You have been warned.

We are going to assume that your sd-card is `/dev/mmcblkX`. Note that we are not
using partitions, but the whole device.

```sh
$ wget https://github.com/sam-itt/gentoo-pie/releases/download/0.0.1/sdcard-gentoo.img.xz
$ wget https://github.com/sam-itt/gentoo-pie/releases/download/0.0.1/sdcard-gentoo.img.sha1
$ sha1sum -c sdcard-gentoo.img.xz.sha1
sdcard-gentoo.img.xz: OK
# xzcat sdcard-gentoo.img.xz > /dev/mmcblkX && sync
```

You can now put the card in your Pi and boot. Login/passwords are:

* pi/pi
* root/pi

## Installed packages
Here is a list of installedpackages on top of the default @system set:

### Misc
* app-misc/pfetch

### Devel:
* sys-devel/gdb
* app-editors/vim
* dev-libs/glib
* dev-vcs/git
* media-libs/libsdl2 (custom ebuild, Rpi OpenGL ES +udev for X-less OpenGL and keyboard)
* media-libs/sdl2-image
* media-libs/sdl2_gpu
* media-libs/raspberrypi-userland (native broadcom OpenGL ES etc.)
* sci-geosciences/gpsd
* sys-apps/i2c-tools

### Gentoo system:
* sys-devel/distcc
* app-portage/eix
* app-portage/gentoolkit

### System:
* net-misc/dhcpcd
* net-misc/ntp
* net-misc/telnet-bsd
* sys-apps/rng-tools
* sys-power/cpupower



[1]: https://github.com/sam-itt/gentoo-pie/blob/media/gentoo-pie-pfetch.png?raw=true
[2]: https://github.com/sam-itt/sofis
