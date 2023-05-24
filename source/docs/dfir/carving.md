# Carving tools

Also see [Steganography tools](../steganography/README.md).

* [foremost](https://github.com/korczis/foremost) is a simple and effective command line interface (CLI) tool that recovers files by reading their headers and footers.
* [recoverjpeg](https://rfc1149.net/devel/recoverjpeg.html) can be used to recover `.jpg` images. The recovered files will be saved in the Home folder and will not have their original names, but instead will be named in numerical order, starting from `00000.jpg`.
* [scalpel](https://salsa.debian.org/pkg-security-team/scalpel), created as an improvement of a much earlier version of `foremost`, aims to address the high CPU and RAM usage issues of foremost when carving data. Unlike foremost, file types of interest must be specified by the investigator in the `scalpel` configuration file (`etc/scapel/scalpel.conf`).
* [photorec](https://www.cgsecurity.org/wiki/PhotoRec)  is a file carving tool, able to recover lost files including video, documents and archives from hard disks (Mechanical Hard drives, Solid State Drives...), CD-ROMs, and lost pictures (thus the Photo Recovery name) from digital camera memory. It is a companion program to [TestDisk](https://www.cgsecurity.org/wiki/TestDisk), an application for recovering lost partitions on a wide variety of file systems and making non-bootable disks bootable again.
* [bulk_extractor](https://github.com/simsong/bulk_extractor) extracts additional types of information that can be very useful in investigations, such as histograms of disk images, email addresses, credit card numbers, urls visited (or bookmarked), online searches, social media profiles, etc.
* [bstrings](https://github.com/EricZimmerman/bstrings) is an improved strings utility
* [floss](https://github.com/fireeye/flare-floss) is a static analysis tool to automatically deobfuscate strings from malware binaries.
* [swap_digger](https://github.com/sevagas/swap_digger) is a bash script used to automate Linux swap analysis, automating swap extraction and searches for Linux user credentials, Web form credentials, Web form emails, etc.
