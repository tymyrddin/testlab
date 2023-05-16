# tcpdump

[tcpdump](https://www.tcpdump.org/) is a command-line utility for capturing and inspecting network traffic going to and from a system.

The packet capture utility used by tcpdump is provided by libpcab, which is a C/C++ library of procedures. The main tcpdump program is the interface for the packet capture process. When run, it will start the libcap process to capture network packets and then display their contents on the screen. Unless a limit to the number of packets to be captured is specified when the program starts, it will continue to run forever. The processing is then terminated by an interrupt signal (Control-C).

