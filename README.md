# debian-rpi
Debian armhf, armel, and arm64 for all Raspberry Pi models

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

See Releases tab for armv6hf image.



# Raspberry Pi Image Generator Scripts

Debian Stretch image builder for Raspberry Pi (all versions) (32-bit only).

Based on worky by Klaus M Pfeiffer, http://www.kmp.or.at/~klaus/raspberry/build_rpi_sd_card.sh

script will:
  - create, partition and format an image
  - install and configure base debian jessie system with Open SSH server
  - download rpi-update which will install the nescessary firmware and bootloader for RPi3 (wifi & bt also)
  - install a first-run script that will re-configure SSH server keys and resize partition to fill the disk on the first run.

### Requirements

Debian/Ubuntu/Kali.... host with the following packages installed:

```binfmt-support qemu qemu-user-static debootstrap kpartx lvm2 dosfstools```

### Usage

Optionally, replace id_rsa.pub file with a link to your ssh public key (most likely ~/.ssh/id_rsa.pub) if you want to log into the RPi with your keypair.

```sudo ./build_image-XXXX.sh ```

You can pass block_device (/dev/mmcblk0) to create the image directly on a card, or specify image_file you would like to create. If neither is given, an image file called rpi_basic_jessie_$(date).img will be created. You can write this image to a card using dd or other tools.

root and pi password is ```raspberry```

Support generation of Debian with armhf or armel (no arm64 yet). 

Only works on a full linux kernel with a Debian-based system....do not bother trying on WSL --> does not work.
