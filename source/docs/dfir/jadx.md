# jadx

[jadx](https://github.com/skylot/jadx), the Dex to Java decompiler, is a command line and GUI tools for producing Java source code from Android Dex and APK files.

## Installation on debian/ubuntu

Get the latest version tag:

```text
$ JADX_VERSION=$(curl -s "https://api.github.com/repos/skylot/jadx/releases/latest" | grep -Po '"tag_name": "v\K[0-9.]+')
$ echo $JADX_VERSION
1.4.7
```

Download the `zip` from the releases page of the repository:

```text
$ curl -Lo jadx.zip "https://github.com/skylot/jadx/releases/latest/download/jadx-${JADX_VERSION}.zip"
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
100 28.5M  100 28.5M    0     0  5085k      0  0:00:05  0:00:05 --:--:-- 6171k
$ ls
 jadx.zip
```

Unzip archive:

```text
$ unzip jadx.zip -d jadx-temp
Archive:  jadx.zip
  inflating: jadx-temp/NOTICE        
   creating: jadx-temp/lib/
  ...      
  inflating: jadx-temp/README.md
```

Move the files: 

```text
$ sudo mkdir -p /opt/jadx/bin 
$ sudo mv jadx-temp/bin/jadx /opt/jadx/bin
$ sudo mv jadx-temp/bin/jadx-gui /opt/jadx/bin
$ sudo mv jadx-temp/lib /opt/jadx
$ cd /opt/jadx
/opt/jadx$ ls
bin  lib
/opt/jadx$ cd bin
/opt/jadx/bin$ ls
jadx  jadx-gui
```

`jadx` is the command line version and `jadx-gui` the UI version.

Add the `/opt/jadx/bin` directory to the `PATH` environment variable in `/etc/profile` to make `jadx` and `jadx-gui` system-wide available:

```text
$ echo 'export PATH=$PATH:/opt/jadx/bin' | sudo tee -a /etc/profile
export PATH=$PATH:/opt/jadx/bin
$ source /etc/profile
$ jadx --version
1.4.7
```

Clean up:

```text
$ rm -rf jadx.zip
$ rm -rf jadx-temp
```

Test:

```text
$ sudo curl -o test.apk https://raw.githubusercontent.com/appium-boneyard/sign/master/tests/assets/tiny.apk
$ jadx test.apk
```

The results are to be in a directory named `test`.

To uninstall, delete the installation directory:

```text
$ sudo rm -rf /opt/jadx
```

And remove the `PATH` entry from `/etc/profile`:

```text
$ sudo sed -i '/export PATH=\$PATH:\/opt\/jadx\/bin/d' /etc/profile
$ source /etc/profile
```

## Usage

In most cases `jadx` can't decompile all 100% of the code, so errors will occur. Check the [Troubleshooting guide](https://github.com/skylot/jadx/wiki/Troubleshooting-Q&A#decompilation-issues) for workarounds.
