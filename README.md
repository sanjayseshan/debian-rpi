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



Instructions for arm64 (no current script):<br>
See releases tab for debian version with everything working! Wifi and BT!
To derive your own image see: https://wiki.gentoo.org/wiki/Raspberry_Pi_3_64_bit_Install
You have to convert the instructions to work with Debian.




