# Linux artifact analysis tools

## Analysis of storage layout and volume management

Logical Volume Manager (LVM) can be used on Linux to manage hard drives and other storage devices. It can sort raw storage into logical volumes, making it easy to configure and use. To use LVM2 you need device-mapper in the kernel, the userspace device-mapper support library (`libdevmapper`) and the userspace lvm2 tools. It is [pre-installed on Kali](https://www.kali.org/tools/lvm2/).

The pvdisplay tool is part of the lvm2 tools and displays various attributes of physical volume(s) (information about the PVs). The `--foreign` flag includes volumes that would normally be skipped and `--readonly` reads data directly from the disk (ignoring the kernel device mapper driver). The `--maps` flag provides additional details about the segments and extents. Information about extents can be helpful for calculating the first sector of the filesystem.

For a linear single disk LVM system in which the filesystem is stored as a continuous sequence of sectors, using this sector offset from the beginning of the physical drive standard allows for the use of standard forensic tools.

`fsstat` provides information about filesystems. An alternative to calculating the start of the filesystem is to search for the start of the filesystem exhaustively (using tools like `gpart`). The `vgdisplay` and `pvs` commands can be used with one or more `-v` flags for additional verbose information about volume groups and physical volumes.