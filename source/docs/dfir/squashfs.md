# SquashFS and fsfimage

The primary advantage of using OSS in a forensic context is transparency. Unlike proprietary commercial software, the source code can be reviewed and openly validated. In addition, researchers can study it and build on the work of others in the community.

The technique described here uses SquashFS as a forensic evidence container together with a small shell script, `sfsimage`, which manages aspects of the container. This method creates a compressed image combined with imaging logs, information about the disk device, and any other information(photographs, chain of custody forms, and so on) into a single package. The files are contained in a read-only SquashFS filesystem, which can be accessed without any special forensic tools.

## Loop devices

The basis for many methods is the Linux loop device, a pseudo device that can be associated with a regular file, making the file accessible as a block device in `/dev`.

While being a virtual file system, there are endless possibilities; here are some widely known use cases of loop devices:

* It can be used to install an operating system over a file system without going through repartitioning the drive.
* A convenient way to configure system images (after mounting them).
* Provides permanent segregation of data.
* It can be used for sandboxed applications that contain all the necessary dependencies.

If you are an Ubuntu user, then you’ll have a long list of loop devices, because of snaps, the universal package management system developed by Canonical. The snap applications are mounted as loop devices.

If not that, Linux systems typically create eight loop devices by default, which might not be enough for a forensic acquisition host, but this number can be increased on boot up. To create 32 loop devices during boot up, add `max_loop=32` to the `GRUB_CMDLINE_LINUX_DEFAULT=` line in the `/etc/default/grub` file:

```shell
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash max_loop=32"
```

After reboot, 32 unused loop devices should be available. The `sfsimage` script uses loop devices to mount SquashFS forensic evidence containers.

## SquashFS

SquashFS is a highly compressed, read-only filesystem written for Linux. It was created by Phillip Lougher in 2002 and was merged into the Linux kernel tree in 2009, starting with kernel version 2.6.29.

* It is read-only; items can be added but not removed or modified.
* It stores investigator’s uid/gid and creation timestamps.
* It supports very large file sizes (theoretically up to 16EiB).
* It is included in the Linux kernel and trivial to mount as a read-only filesystem.
* The filesystem is an open standard (tools exist for Windows, OS X).
* The `mksquashfs` tool uses all available CPUs to create a container.

Using SquashFS as a forensic evidence container is a practical alternative to using other forensic formats, because it facilitates the management of compressed raw images acquired with `dd`. 

## sfsimage

The [sfsimage](https://digitalforensics.ch/sfsimage/) tool provides the functionality to manage SquashFS forensic evidence containers. To configure it, you can edit the script or create separate `sfsimage.conf` files. The config file is documented with comments and examples, and it allows defining:

* Preferred imaging/acquisition command (`dd`, `dcfldd`, `dc3dd`, ...)
* Preferred command to query a device (`hdparm`, `tableu-parm`, ...)
* Default directory to mount the evidence container (the current working directory is the default)
* How to manage privileged commands (`sudo`, `su`, ...)
* Permissions and uid/gid of created files

To image a disk into a SquashFS forensic evidence container, run `sfsimage` using the `-i` flag, the disk device, and the name of the evidence container:

```shell
sfsimage -i /dev/sde containername.sfs
```

To add additional evidence to a container, use the `-a` flag:

```shell
sfsimage -a photo.jpg containername.sfs
```

List the contents of the container with the `-l` flag:

```shell
sfsimage -l containername.sfs
```

This command output shows the contents of the `containername.sfs` container (without mounting it). Also shown are the correct times when the files were created or added. The error log, hash log, and sfsimage log contain documentation about activity and errors.

Mount the container with the `-m` flag:

```shell
sfsimage -m containername.sfs
```

```shell
containername.sfs.d mount created
```

When the mount is no longer needed, unmount it with the `-u` flag:

```shell
sfsimage -u containername.sfs.d
```
