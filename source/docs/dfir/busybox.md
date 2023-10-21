# BusyBox

BusyBox is an open source project that provides a stripped down implementation of around 400 common UNIX/Linux commands. It runs in a variety of POSIX environments such as Linux, Android, and FreeBSD, and is used in dockers. 

## Installation

On android:

[Download](https://www.appsapk.com/busybox-app/) and install busybox apk:

```text
adb -d install BusyBox.apk
```

## Usage example in Android forensics

1. Check root access:

```text
su
# ls /data
```

2. Check the mounted partitions on the device:

```text
mount
```

Choose the partitions you wish to image and note their paths, for example for the data partition, something like `/dev/block/bootdevice/by-name/userdata`.

Set up connection between the workstation and the mobile device, forwarding port `8080`:

Workstation:

```text
adb forward tcp:8080 tcp:8080
```

Mobile device:

```text
dd if=/dev/block/bootdevice/by-name/userdata | busybox nc -l -p 8080
```

Workstation:

```text
nc 127.0.0.1 8080 > android_data.dd
```

Start analysis on the image disk, using sleuthkit tools or Autopsy.