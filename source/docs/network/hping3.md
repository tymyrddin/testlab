# hping3

[hping3](https://www.kali.org/tools/hping3/) is a network tool able to send custom ICMP/UDP/TCP packets and to display target replies like ping does with ICMP replies. It handles fragmentation and arbitrary packet body and size, and can be used to transfer files under supported protocols. 

hping3 can test firewall rules, perform (spoofed) port scanning, test network performance using different protocols, do path MTU discovery, perform traceroute-like actions under different protocols, fingerprint remote operating systems, audit TCP/IP stacks, etc. 

hping3 is scriptable in the Tcl scripting language, and it can render packets into strings-based, human-readable descriptions for ease of writing scripts to perform low-level packet manipulation and analysis. It can also be used to spoof source IP addresses and generate large amounts of traffic in order to explore various DDoS techniques (a very common use case during network pentesting).

## Cheatsheets

* [Getting started with hping3](http://wiki.hping.org/94)
* [Man hping3](https://linux.die.net/man/8/hping3)