# A build of Gentoo for Raspberry Pi 1 and zero

![shell screenshot](https://github.com/sam-itt/gentoo-pie/blob/media/gentoo-pie-pfetch.png)

Bootable image with minimal system and some dev tools. The main purpose of this
build is to serve as a base system for [SoFIS](https://github.com/sam-itt/sofis).

However it can be used for virtually anything. Here is a list of installed
packages on top of the default @system set:

## Misc
* app-misc/pfetch

## Devel:
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

## Gentoo system:
* sys-devel/distcc
* app-portage/eix
* app-portage/gentoolkit

## System:
* net-misc/dhcpcd
* net-misc/ntp
* net-misc/telnet-bsd
* sys-apps/rng-tools
* sys-power/cpupower

