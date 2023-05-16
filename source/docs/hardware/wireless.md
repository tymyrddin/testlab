# Wireless adapters for monitoring

* [HAK5 WIFI pineapple](https://shop.hak5.org/products/wifi-pineapple) 
* [MK7AC WiFi Adapter](https://shop.hak5.org/products/mk7ac-wifi-adapter)

## Alternative adapters

If your wireless adapter fails to go into monitor mode in Kali, try killing processes with `rfkill unblock all`. 
Then try to put the adapter in monitor mode. If it still doesn’t work, your wireless adapter may not support monitor 
mode.

### Atheros chipset AR9271

This chipset supports monitor mode and packet injection, and can also be used to create a fake access point or to hack 
into networks. But it only supports 2.4 gigahertz, which means that if your target uses 5 gigahertz or some of the 
devices are connected over 5G, you will be unable to communicate with these devices.

You can either get an unbranded wireless adapter that uses this chipset, or the Alpha AWUS036NHA wireless adapter. 
It has the same chipset, will be backward compatible, has a longer range and is more reliable.

### Realtek chipset RTL8812AU

This chipset was supported by Kali Linux in 2017, and it supports monitor mode, packet injection, and frequencies of 
2.4 and 5 gigahertz, but is everything but reliable. As with the above chipset you can get a budget wireless adapter, 
or the AWUS036AC. The Alpha is expensive and bigger, the budget version less powerful and more compact, hence raises 
fewer suspicions in public.

## Kali VM notes

Make sure that the Network settings are adjusted by bridging the Kali VM to your router. 
Kali Linux will look for an IP address from your DHCP server by default, but it is recommended
to assign a static IP address to avoid confusion.