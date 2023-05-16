# NetworkMiner

| **Capability**                 | **Description**                                                                                                                                                                   |
|:-------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Traffic sniffing**           | It can intercept the traffic, sniff it, and collect and log packets that pass <br>through the network.                                                                            |
| **Parsing PCAP files**         | It can parse pcap files and show the content of the packets in detail.                                                                                                            |
| **Protocol analysis**          | It can identify the used protocols from the parsed pcap file.                                                                                                                     |
| **OS fingerprinting**          | It can identify the used OS by reading the pcap file. This feature strongly <br>relies on[ Satori ](https://github.com/xnih/satori/)and [p0f](https://lcamtuf.coredump.cx/p0f3/). |
| **File Extraction**            | It can extract images, HTML files and emails from the parsed pcap file.                                                                                                           |
| **Credential grabbing**        | It can extract credentials from the parsed pcap file.                                                                                                                             |
| **Clear text keyword parsing** | It can extract clear-text keywords and strings from the parsed pcap file.                                                                                                         |

**A Professional edition has much more features. You can see the differences between free and professional versions** [**here**](https://www.netresec.com/?page=NetworkMiner)**.**

## Operating modes

- **Sniffer Mode:** Although it has a sniffing feature, it is not intended to use as a sniffer. The  sniffier feature is available only on Windows. However, the rest of the  features are available in Windows and Linux OS. Based on experience, the sniffing feature is not as reliable as  other features. Therefor we suggest not using this tool as a primary sniffer. Even the official description of the tool mentions that this  tool is a "Network forensics Analysis Tool", but it can be used as a  "sniffer". In other words, it is a Network Forensic Analysis Tool with  but has a sniffer feature, but it is not a dedicated sniffer like  Wireshark and tcpdump.
- **Packet Parsing/Processing:** NetworkMiner can parse traffic captures to have a quick overview and information on  the investigated capture. This operation mode is mainly suggested to  grab the "low-hanging fruit" before diving into a deeper investigation.

## Pros and cons

### Pros

- OS fingerprinting
- Easy file extraction
- Credential grabbing
- Clear text keyword parsing
- Overall overview

### Cons

- Not useful in active sniffing
- Not useful for large pcap investigation
- Limited filtering
- Not built for manual traffic investigation

## Differences between Wireshark and NetworkMiner

NetworkMiner and Wireshark have similar base features, but are different in purpose. 

Best practice is to record the traffic for offline analysis, quickly overview the pcap with NetworkMiner and then use Wireshark for further investigation.

| **Feature**                 | **NetworkMiner**                                         | **Wireshark**     |
|:----------------------------|----------------------------------------------------------|-------------------|
| Purpose                     | Quick overview, traffic mapping, <br>and data extraction | In-Depth analysis |
| GUI                         | **✅**                                                    | **✅**             |
| Sniffing                    | **✅**                                                    | **✅**             |
| Handling PCAPS              | **✅**                                                    | **✅**             |
| OS Fingerprinting           | **✅**                                                    | ❌                 |
| Parameter/Keyword Discovery | **✅**                                                    | Manual            |
| Credential Discovery        | **✅**                                                    | **✅**             |
| File Extraction             | **✅**                                                    | **✅**             |
| Filtering Options           | Limited                                                  | **✅**             |
| Packet Decoding             | Limited                                                  | **✅**             |
| Protocol Analysis           | ❌                                                        | **✅**             |
| Payload Analysis            | ❌                                                        | **✅**             |
| Statistical Analysis        | ❌                                                        | **✅**             |
| Cross-Platform Support      | **✅**                                                    | **✅**             |
| Host Categorisation         | **✅**                                                    | ❌                 |
| Ease of Management          | **✅**                                                    | **✅**             |

## NetworkMiner version differences

Unsurprisingly version upgrades provide stability, security fixes and features. For NetworkMiner the feature part is 
quite tricky. Feature upgrades can represent implementing new features and updating  the existing feature 
(optimisation, alteration or operation mode modification). You can always 
[check the changelog](https://www.netresec.com/?page=NetworkMiner).

Of course, as the program version increases, it is expected to increase feature increase and scope. 
The significant differences between versions 1.6 and 2.7:

### Mac address processing

NetworkMiner versions after version 2 can process MAC address specific correlation. This option can help identify if there is a MAC Address conflict. This feature is not available before version 2.

### Sent/received packet processing

NetworkMiner versions up to version 1.6. can handle packets in much detail. These options can help investigate the sent/received packets in a more detailed format. This feature is not available after version 1.6.

### Frame processing

NetworkMiner versions up to version 1.6. can handle frames. This option provides the number of frames and essential details about the frames. This feature is not available after version 1.6.

### Parameter processing

NetworkMiner versions after version 2 can handle parameters in a much more extensive form. Therefor version 1.6.xx catches fewer parameters than version 2.

### Clear-text processing

NetworkMiner versions up to version 1.6. can handle clear-text data. This option provides all extracted clear-text data in a single tab; it is beneficial to investigate clear-text data about the traffic data. However, it is impossible to match the clear-text data and packets. This feature is not available after version 1.6.

**Since there are some significant differences between the versions, the given VM has both of the major versions (v1.6 and v2.7).**
