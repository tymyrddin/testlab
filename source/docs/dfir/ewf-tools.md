# Libewf and ewf-tools

[Libewf](https://github.com/libyal/libewf) is an open source library (for Linux and OSx) that supports reading and writing EWF (Expert Witness Compression Format) formats. 

It supports reading media information of EWF files in the SMART (EWF-S01) format and the EnCase (EWF-E01) format. It supports files created by EnCase 1 to 6, linen and FTK Imager. It contains tools to acquire, verify and export EWF files.

The library contains:

* `ewfacquire` acquires data in the EWF format.
* `ewfacquirestream` acquires data in the EWF format from stdin.
* `ewfdebug` supports analysis of EWF files.
* `ewfexport` exports data from the EWF format to raw data or another EWF format.
* `ewfinfo` gives information about the EWF format.
* `ewfmount` can mount an EWF image file.
* `ewfrecover` can recover data from corrupt EWF files.
* `ewfverify` can verify data stored in the EWF format.
* `libewf-dev` and libewf2.
* `python3-libewf` contains Python 3 bindings for libewf.

## Installation

```text
sudo apt install libewf-dev ewf-tools
```

## Usage

To acquire a disk image (The `-t` switch is for destination):

```text
sudo ewfacquire -t /path/to/case /dev/sdm
```

Any arguments that were not added in the command line, will have to be answered through questions, like segment file size `-S`, for example to `-S 4G`. When using the `-u` flag for unattended mode, all arguments would need to be set at the command line.

Check the result `ewfinfo` and `ewfverify`:

```text
ewfinfo /path/to/case.E01
ewfverify /path/to/case.E01
```

After mounting, tools that do not support EWF can get access to the disk or mounted partitions.

To mount the disk image to provide direct access to the copied disk:

```text
sudo mkdir /mnt/ewf
sudo chown [username] /mnt/ewf
ewfmount //path/to/case.E01 /mnt/ewf
cd /mnt/ewf
```

The device inside `/mnt/ewf` is the physical or logical disk image, depending on which source image was made, and the device can be accessed with other tools.

## Resources

* [Manpages of ewf-tools in Debian unstable](https://manpages.debian.org/unstable/ewf-tools/index.html)