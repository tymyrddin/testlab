# Human interface devices

The HID standard was adopted primarily to enable innovation in PC input devices and to simplify the process of installing such devices. All HID-defined devices deliver self-describing packages that may contain any number of data types and formats. A single HID driver on a computer parses data and enables dynamic association of data I/O with application functionality, which has enabled rapid innovation and development, and prolific diversification of new human-interface devices. Most mainstream operating systems will recognize standard USB HID devices, such as keyboards and mice, without needing a specialised driver.

BadUSB is a computer security attack using USB devices that carry a scripted payload. For example, USB flash drives can contain a programmable microcontroller, which can be reprogrammed, turning a USB flash drive into a malicious device. The firmware of a USB device can only be read back with the help of that same firmware. A malicious firmware can spoof a legitimate one. 

## Gadgets

The [USB Rubber Ducky](https://hak5.org/products/usb-rubber-ducky?variant=353378649) is coupled with a powerful 60 MHz 32-bit processor and a simple scripting language anyone is able to craft [payloads](https://github.com/hak5/usbrubberducky-payloads) capable of changing system settings, opening backdoors, retrieving data, initiating reverse shells, or basically anything that can be achieved with physical access. [Bash Bunny](https://hak5.org/products/bash-bunny), also by hak5, takes it further as a [payload](https://github.com/hak5/bashbunny-payloads) platform for multi-vector USB attacks.

Flipper Zero is a portable Tamagotchi-like multi-functional device (hand-held digital pet), developed for interaction with access control systems. The device is able to read, copy, and emulate RFID and NFC tags, radio remotes, iButton, and digital access keys, along with a GPIO interface. Using it for [payloads](https://github.com/UNC0V3R3D/Flipper_Zero-BadUsb) is extremely easy. And some people [take it to first place](https://github.com/I-Am-Jakoby/Flipper-Zero-BadUSB).

[Teensy](https://www.pjrc.com/teensy/) is like a rubber ducky, but cheaper. It hides as a keyboard. 

The [O.MG cable](https://shop.hak5.org/collections/mischief-gadgets/products/omg-adapter?variant=39914370334833) from [MG](https://mg.lol/blog/omg-cable/) hides a backdoor inside the shell of a USB connector. Plug this cable into a computer it’ll be the victim of remote attacks over WiFi. In essence, a BadUSB device that can be remotely controlled.

Next up is a USB-C dock: take a stock dock, find a Raspberry Pi Zero W and wire it up to a USB 2.0 port tapped somewhere inside the dock, and flash the SD card with a [payload image](https://github.com/RoganDawes/P4wnP1_aloa). Finding a Pi Zero is the hardest part.

## Mitigations

Here are three measures that you can implement to counteract BadUSB vulnerability right away.

* Never insert a USB-stick which you do not (fully) trust. Only use USB-sticks which are new and sealed and you can verify the origin. Do not plug in any USB sticks which you found.
* Implement Admin Rights Management (ARM). Users will have to re-enter user credentials to start cmd or PowerShell, making most BadUSB scripts fail.
* Configure only allowing signed scripts to be run.
* Only allow HID devices based on known and trusted ID numbers or block VID value `0x2341` and PID value `0x8037`. (still vulnerable to physical tampering if not monitored)
* Disable USB ports in the BIOS/EUFI if a machine does not need USBs for daily operations
* SIEM/SOC Monitor typing speed (But it may already be too late)
* IDS and an IPS (already spawned/too late)
