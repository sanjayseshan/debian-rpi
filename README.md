# debian-rpi
Debian armhf, armel, and arm64 (coming soon) for all Raspberry Pi models

THIS IS A MINIMAL IMAGE ONLY

Requirements:

~2 GB of disk space and a Debian (or derivitive - eg. Ubuntu) host

run:

sudo apt-get install binfmt-support qemu qemu-user-static debootstrap kpartx lvm2 dosfstools

sudo ./APPROPRITE_FILE_FOR_PI_VERSION_HERE.sh

Supports:<br>
All basic features (audio, video, gpio(with rpi-gpio python installed, wifi, bluetooth))<br>
Pi3 bluetooth and wifi
<br>
Todo:
Get basic arm64 image for pi3 working (no firmware currently avaliable in arm64 mode)



Instructions for arm64 (no current script):<br>
make 64mb fat partition on sdcard and rest as ext4<br>
debootstrap arch=arm64 --foreign jessie ./
64-bit Raspberry Pi 3 kernel status is in its early days as of this writing (May 2016). The only known general-purpose working kernel is a 4.5.0 kernel from user "Electron752". Raspberry Pi firmware is working in 64-bit mode as of late April (with arm_control=0x200), and u-boot's 64-bit rpi_3 target is working as of version 2016.05.

Some forum posts describe building a "stubbed" u-boot which tells the RPi3 to switch to 64-bit mode, but this is no longer required with latest firmware and u-boot.

You may use 20160517-raspi3-arm64-firmware-kernel.tar.xz and manually integrate it into an Ubuntu arm64 userland installation. It's a tree consisting (only) of:

4.5.0+ kernel and modules from https://github.com/Electron752/boot64-rpi3 (place in fat partition)
u-boot binary from u-boot 2016.05~rc3+dfsg1-1rpi3.2 (lp:ubuntu-raspi2/ppa-rpi3)
Firmware from linux-firmware-raspi2 1.20160503+6832d9a-0ubuntu1~rpi3 (lp:ubuntu-raspi2/ppa-rpi3)
Known issues:

brcmfmac does not seem to recognize the 43430 wifi/bluetooth controller, even with firmware present.
The kernel requires a custom DTB. Therefore u-boot loads and uses the standard bcm2710-rpi-3-b.dtb (same one compiled from the Ubuntu 4.4.0 kernels), then loads the custom DTB, overwriting 0x100 before handing off to Linux.
Make sure flash-kernel (even the version from ppa:ubuntu-raspi2/ppa-rpi3) is not installed, as it will replace boot.scr with one which doesn't have the DTB loading hack.
VideoCore userland utilities are not yet available for arm64.

--Ubuntu
