# T-Pot framework

[T-Pot](https://github.com/telekom-security/tpotce) is an All-In-One Multi Honeypot Platform, supporting 20+ 
honeypots and countless visualisation options using the Elastic Stack, animated live attack maps and lots of 
security tools to further improve the deception experience.

## TL;DR

* Meet the [system requirements](https://github.com/telekom-security/tpotce#system-requirements). The T-Pot installation needs at least 8-16 GB RAM and 128 GB free disk space as well as a working (outgoing non-filtered) 
internet connection.
* Download the T-Pot ISO from [GitHub](https://github.com/telekom-security/tpotce/releases) according to your architecture (amd64, arm64) or [create it yourself](https://github.com/telekom-security/tpotce#create-your-own-iso-image).
* Install the system in a [VM](https://github.com/telekom-security/tpotce#running-in-a-vm) or on[physical hardware](https://github.com/telekom-security/tpotce#running-on-hardware) with [internet access](https://github.com/telekom-security/tpotce#system-placement).
* Enjoy your favorite beverage - [watch](https://www.sicherheitstacho.eu/start/main) and [analyse](https://github.com/telekom-security/tpotce#kibana-dashboard). 

## Honeypot dockers

T-Pot offers docker images for the following honeypots:

### Databases

* [ElasticPot](https://gitlab.com/bontchev/elasticpot) - A honeypot simulating a vulnerable Elasticsearch server 
opened to the Internet.
* [RedisHoneyPot](https://github.com/cypwnpwnsocute/RedisHoneyPot) - High Interaction Honeypot Solution for Redis protocol.

### Email

* [Mailoney](https://github.com/phin3has/mailoney) - SMTP honeypot, Open Relay, Cred Harvester written in python.

### ICS/SCADA

* [Conpot](https://github.com/mushorg/conpot) - An ICS honeypot with the goal to collect intelligence about the motives and methods of adversaries targeting industrial control systems.

### Mobile

* [Android Debug Bridge over TCP/IP](https://github.com/huuck/ADBHoney) - Low interaction honeypot that simulates an Android device running Android Debug Bridge (ADB) server process.

### Network services

* [Dionaea](https://github.com/DinoTools/dionaea) - A nepenthes successor, embedding python as scripting language, using libemu to detect shellcodes, supporting ipv6 and tls.
* [Cisco ASA honeypot](https://github.com/Cymmetria/ciscoasa_honeypot) - A low interaction honeypot for the Cisco ASA component capable of detecting CVE-2018-0101, a DoS and remote code execution vulnerability.
* [DDoSPot](https://github.com/aelth/ddospot) - NTP, DNS, SSDP, Chargen and generic UDP-based amplification DDoS honeypot.

### Other

* [CitrixHoneypot](https://github.com/MalwareTech/CitrixHoneypot) - Detect and log CVE-2019-19781 scan and exploitation attempts.
* [Dicompot](https://github.com/nsmfoo/dicompot) - DICOM Honeypot.
* [Log4Pot](https://github.com/thomaspatzke/Log4Pot) - A honeypot for the Log4Shell vulnerability (CVE-2021-44228).
* [medpot](https://github.com/schmalle/medpot) - HL7 / FHIR honeypot.

### Server

* [Glutton](https://github.com/mushorg/glutton) - All eating honeypot.
* [Heralding](https://github.com/johnnykv/heralding) - Credentials catching honeypot.

### Service

* [Honeypots](https://github.com/qeeqbox/honeypots) - 25 different honeypots in a single pypi package! (dns, ftp, httpproxy, http, https, imap, mysql, pop3, postgres, redis, smb, smtp, socks5, ssh, telnet, vnc, mssql, elastic, ldap, ntp, memcache, snmp, oracle, sip and irc).
* [Honeytrap](https://github.com/honeytrap/honeytrap) - Advanced Honeypot framework written in Go that can be connected with other honeypot software.
* [IPP Honey](https://gitlab.com/bontchev/ipphoney) - A honeypot for the Internet Printing Protocol.

### SIP

* [SentryPeer](https://github.com/SentryPeer/SentryPeer) - A fraud detection tool which lets bad actors try to make phone calls and saves the IP address they came from and number they tried to call.

### SSH

* [Cowrie](https://github.com/cowrie/cowrie) - Cowrie SSH Honeypot (based on kippo).
* [Endlessh](https://github.com/skeeto/endlessh) - An SSH tarpit.
* [Kippo](https://github.com/desaster/kippo)  - Medium interaction SSH honeypot.

### Web applications

* [HellPot](https://github.com/yunginnanet/HellPot) - Honeypot that tries to crash the bots and clients that visit it's location.
* [Nodepot](https://github.com/schmalle/Nodepot) - NodeJS web application honeypot.
* [SNARE](https://github.com/mushorg/snare) - A web application honeypot sensor, the successor of Glastopf.
* [TANNER](https://github.com/mushorg/tanner) - SNARES' "brain", allowing for changing the behaviour of sensors on the fly. 


