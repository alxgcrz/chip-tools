# CHIP-tools

A collection of scripts for working with CHIP

## Requirements

> `sudo apt -y install build-essential git mercurial cmake curl screen unzip device-tree-compiler libncurses-dev ppp cu linux-image-extra-virtual u-boot-tools android-tools-fastboot android-tools-fsutils python-dev python-pip libusb-1.0-0-dev g++-arm-linux-gnueabihf pkg-config libacl1-dev zlib1g-dev liblzo2-dev uuid-dev sunxi-tools`

## Instructions for flashing process

1. Ensure CHIP is powered off and not connected to the host computer. Put a jumper wire between FEL and GND pins.
1. Clone [CHIP-tools repository](git@github.com:alxgcrz/chip-tools.git) to $HOME/CHIP-tools: `git clone git@github.com:alxgcrz/chip-tools.git $HOME/CHIP-tools`
1. Change to 'CHIP-tools' folder: `cd CHIP-tools`
1. Modify permissions: `sudo chmod 755 *.sh`
1. Execute setup script: `bash setup.sh`
1. Execute `FEL='sudo sunxi-fel' FASTBOOT='sudo fastboot' SNIB=false`
1. Execute tool to flash CHIP:
    * With local firmware: `./chip-update-firmware.sh -L ./stable-server-b149`
    * Downloading remote firmware: `./chip-update-firmware.sh`
1. When "Waiting for fel......" prompt appears, connect CHIP to the host computer with a microUSB cable.
1. When "FLASH VERIFICATION COMPLETE" message appears, flashing is successful.
1. Disconnect CHIP from PC
1. Remove jumper wire between FEL and GND pins.
1. Connect CHIP to host computer again.
1. Wait few seconds
1. Control CHIP Using a Serial Terminal: `screen $(ls -tw 1 /dev/tty* | head -1) 115200`

## Included Tools

### chip-update-firmware

This tool is used to download and flash the latest firmware release for CHIP. The tool also now only supports fastboot flashing.

### chip-create-nand-images

This tool is used to generate local firmware images for CHIP and CHIP Pro.
