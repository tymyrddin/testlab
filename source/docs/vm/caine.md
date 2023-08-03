# Computer aided investigative environment (CAINE)

[CAINE](https://www.caine-live.net/) (Computer aided investigative environment) is a live-response bootable CD/DVD with options for booting in safe mode, text mode, as a live system, or in RAM.

CAINE 13 is based on Ubuntu 22.04 64bit (Kernel 5.15.0-67), and can also be installed as VM.

One of the most noticeable [features of CAINE](https://www.caine-live.net/page11/page11.html) after selecting the boot option is the write-blocker feature (blockdev), labeled as an UnBlock icon, which puts the device in WRITABLE mode. CAINE blocks all the block devices in Read-Only mode. This write-blocking method assures all disks are really preserved from accidentally writing operations, because they are locked in Read-Only mode. To write a disk, you can unlock it with UnBlock or using "Mounter" changing the policy in writable mode. 

## Installation

When installing CAINE in a VM, it is entirely possible that the Unlock GUI does not detect your disk. Use the command-line, for example:

```text
caine@caine:~$ sudo blockdev --setrw /dev/vd*
```

Use boot-repair before rebooting at the end of installation:

```text
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update

sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update

sudo apt-get install -y boot-repair && boot-repair
```

If that doesn't work, manually install grub:

```text
sudo apt-get --allow-releaseinfo-change update

sudo apt-get update

sudo fdisk -l

sudo blkid

sudo mkdir /mnt/ubuntu

sudo mount /dev/vda1 /mnt/ubuntu

sudo grub-install --boot-directory=/mnt/ubuntu/boot /dev/vda
```

## Usage

Forensic tools is the first menu listed in CAINE. There are several categories in the menu, with several of the more popular tools used in open source forensics. Besides the categories, there are direct links to some of the more well-known tools, such as [Guymager](../dfir/guymager.md) and [Autopsy](../dfir/autopsy-kali.md) (In CAINE 13 autopsy 2.24 is installed, to keep the ISO size down).

## Resources

* [man blockdev(8)](https://www.man7.org/linux/man-pages/man8/blockdev.8.html)
* [The Law Enforcement and Forensic Examiner’s Introduction to Linux](https://linuxleo.com/Docs/LinuxLeo-4.96.pdf)