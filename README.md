# Raspberry Pi Image Generator Scripts
Generates debian armhf, armel, and arm64 for all Raspberry Pi models

Requirements:

* ~3 GB of disk space and a Debian (or derivitive - eg. Ubuntu) host

Run (on host):
* `sudo apt-get install binfmt-support qemu qemu-user-static debootstrap kpartx lvm2 dosfstools`
* `sudo ./build_image.sh`
* Use `dd if=debianXX.img of=/dev/mmcblkXX` to flash to sdcard (adjust command to your setup)

~~~
build_image.sh Usage:
 -a | --arch : Build architecture of Raspberry Pi (armel, armhf, or arm64)
 -m | --model : Raspberry Pi Version (rpi1, rpi2, rpi3, rpi0, or rpi4)
 -r | --release : Debian version to use (buster is the oldest for arm64 support and wheezy for armel/armhf) (no support for bullseye yet)
~~~

Supports:
* All basic hardware features (HDMI, audio, analog video, etc.)
* Pi bluetooth and wifi, 4gb ram on rpi4 (8gb should work but I cannot test this)
* raspberrypi vc libs
* GPIO pins (you have to install RPI.GPIO to address them in python)

On raspberry pi:
* Login as `root:raspberry` or `pi:raspberry`
* Run `raspi-config` as root to expand rootfs to full sdcard
* Setup as any other linux system
* openssh-server is pre-installed but you have to connect it to the network
* Install a GUI (optional) using `apt-get install xinit lightdm mate-desktop-environment-core`

Based on work by Klaus M Pfeiffer (http://www.kmp.or.at/~klaus/raspberry/build_rpi_sd_card.sh).
