# KVM on Ubuntu

## Requirement checks

1. To check the machine's CPU supports hardware virtualisation:

```text
egrep -c '(vmx|svm)' /proc/cpuinfo
```

If returns `0`, the processor does not support it. Any other number is ok. Note: `lm` stands for Long Mode which equates to a 64-bit CPU.

2. To check virtualisation is enabled in the BIOS, install `cpu-checker` and check if the system can use kvm acceleration:

```text
sudo apt install cpu-checker
```

```text
sudo kvm-ok
```

The response must include `INFO: /dev/kvm exists`.

If you see :

```text
INFO: Your CPU does not support KVM extensions
KVM acceleration can NOT be used
```

You can still run virtual machines, but it will be incredibly slow. 

## Install essential packages

```text
sudo apt install qemu-kvm libvirt-daemon-system libvirt-clients bridge-utils
```

## Add users to groups

```text
sudo adduser '[username]' libvirt
```

```text
sudo adduser '[username]' kvm
```

Relogin so that `username` becomes an effective member of the `libvirtd` and `kvm` groups. The members of this group can run virtual machines. 

## Verify installation

```text
virsh list --all
```

```text
sudo systemctl status libvirtd
```

If not `active`, enable with:

```text
sudo systemctl enable --now libvirtd
```

## Install virt manager GUI

```text
sudo apt install virt-manager
```

Launch it to create Virtual Machines.
