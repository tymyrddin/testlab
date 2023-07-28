# SIFT with REMnux

Sign in and login to the [SANS site](https://www.sans.org/tools/sift-workstation/), to download the `.ova`.

Unpack:

```text
nina@tardis:~/Downloads$ tar -xvf SIFT-Workstation.ova
sift-vmware-iso-full.ovf
sift-vmware-iso-full.mf
sift-vmware-iso-full-disk1.vmdk
```

Convert the `.vmdk` to `.qcow2`:

```text
nina@tardis:~/Downloads$ qemu-img convert -O qcow2 sift-vmware-iso-full-disk1.vmdk sift-vmware-iso-full-disk1.qcow2
```

Move the `.qcow2` file to `/var/lib/libvirt/images`, and change its owner to `libvirt-Qemu`. Import it as guest VM.

Login = `sansforensics`; Password = `forensics`; Use `$ sudo su -` for privileged commands.

Have it running to add the REMnux components, download the installer for it:

```text
sansforensics@siftworkstation: ~
$ wget https://REMnux.org/remnux-cli
```

Generate the hash of the file:

```text
sansforensics@siftworkstation: ~
$ sha256sum remnux-cli
```

Validate that the SHA-256 hash of the downloaded file to match the expected value:

`23c7f4eefa7599ea2c4156f083906ea5fd99df18f306e4bb43eec0430073985a`

Set up the REMnux installer:

```text
sansforensics@siftworkstation: ~
$ mv remnux-cli remnux
sansforensics@siftworkstation: ~
$ chmod +x remnux
sansforensics@siftworkstation: ~
$ sudo mv remnux /usr/local/bin
```

Make sure the system does not have an active Ubuntu unattended upgrade in progress:

```text
sansforensics@siftworkstation: ~
$ ps aux | grep unattended-upgrade
```

If active, let it finish, or disable it:

```text
sansforensics@siftworkstation: ~
$ systemctl mask unattended-upgrades.service
sansforensics@siftworkstation: ~
$ systemctl stop unattended-upgrades.service
```

Install the REMnux distro:

```text
sansforensics@siftworkstation: ~
$ sudo remnux install --mode=addon
```

The `addon` mode will avoid modifications that can modify the look and feel of the existing system. The installation will take about an hour, depending on available resources and internet connection. Reboot the  REMnux System:

```text
sansforensics@siftworkstation: ~
$ sudo reboot
```

Take a Snapshot of the Virtual Machine. 
