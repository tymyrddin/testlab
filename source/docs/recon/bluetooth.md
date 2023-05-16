# Tools for Bluetooth device discovery

* `hciconfig`, a command used to configure Bluetooth devices, can initiate a Bluetooth interface:

```text
hciconfig hci0 up
```

* `hcitool`, a command used to configure Bluetooth connections. To run a low-energy scan:

```text
sudo hcitool lescan
```

* `bluesniff` can discover Bluetooth devices.
* `sdptool` queries Bluetooth devices and helps in configuring permissions.

```text
sdptool browser <bluetooth-address>
```

* `gatttool` can be used to analyze Bluetooth Low-Energy (BLE) devices. The BLE address of the target must be known:

```text
sudo gatttool -I -b <BLE-Address>
```

* `ubertooth-btle` is used to sniff BLE packets.
* `btscanner` can scan Bluetooth devices.