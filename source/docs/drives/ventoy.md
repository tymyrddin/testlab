# Ventoy

[Ventoy](https://www.ventoy.net/en/index.html) is a bootable USB solution that lets you copy-paste an image to create a live USB drive, and can be used to use it to create a multiboot USB. 


You only have to install Ventoy to the USB drive, which makes two separate partitions. One of the partitions is used to store ISO images that you can  paste into the USB drive to make it bootable. 

There is no need to reformat the disk to update it with new installation files; it is enough to copy the `.iso`,`.wim`,`.img`, or `.efi` file to the USB drive and boot from them directly. Ventoy will present the user with a boot menu to select one of these files.

## Installation

It is [available for Windows and Linux](https://github.com/ventoy/Ventoy/releases).

1. Right-click on the `VentoyGUI.x86_64` file and, then on `Run`. That will open up an authentication screen, type in the password of your local user and the GUI tool will launch. Ventoy usually automatically detects the USB but still make sure that the intended USB disk is selected in the tool. Click on the **Install**.
2. The drive will have two partitions. `VTOYEFI` is reserved for the boot files, and an exFAT partition for copying the ISO files to.
3. After copying, do not unplug the USB. Use the Unmount or Eject option.

I have put caine 13, caine 11 (for its Autopsy) and a kali live iso on it.


