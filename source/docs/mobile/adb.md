# Android Debug Bridge (ADB)

The [Android Debug Bridge (ADB)](https://developer.android.com/studio/command-line/adb) is a command-line utility included with [Google’s Android SDK](android-sdk.md) for debugging Android-based devices. 

`adb` can control a device over USB from a computer, copy files back and forth, install and uninstall apps, run shell commands, etc. It is part of the [SDK Platform Tools](https://developer.android.com/studio/releases/platform-tools)

The daemon on the Android device communicates with the server on the host PC through USB or TCP, which communicates with the end-client users via TCP.

## Installation

    sudo apt update
    sudo apt -y install android-tools-adb

## Usage

1. Open a terminal window.
2. Pull the hosts file out of the phone to your PC.
3. Edit it.
4. disable READ_ONLY of SYSTEM

```text
$ su
# mount -o rw,remount /system
```

5. Push the file back.
6. Put SYSTEM back to READ_ONLY: 

```text
# mount -o ro,remount /system
```
