# Brim

Brim is an open-source desktop application that processes pcap files and logs files, with a primary focus on providing search and analytics. It uses the Zeek log processing format. It also supports Zeek signatures and Suricata Rules for detection.

It can handle two types of data as an input;

* Packet Capture Files:  Pcap files created with tcpdump, tshark and Wireshark like applications.
* Log Files:  Structured log files like Zeek logs.

Brim is built on open-source platforms:

* Zeek: Log generating engine.
* Zed Language: Log querying language that allows performing keyword searches with filters and pipelines.
* ZNG Data Format: Data storage format that supports saving data streams.
* Electron and React: Cross-platform UI.

## Brim vs Wireshark vs Zeek

The common best practice is handling medium-sized pcaps with Wireshark, creating logs and correlating events with Zeek, and processing multiple logs in Brim.

|                             | Brim                                                       | Wireshark                                                                    | Zeek                                                       |
|:----------------------------|------------------------------------------------------------|------------------------------------------------------------------------------|------------------------------------------------------------|
| Purpose                     | Pcap processing;<br>event/stream and log<br>investigation. | Traffic sniffing.<br>Pcap processing;<br>packet and stream<br>investigation. | Pcap processing;<br>event/stream and log<br>investigation. |
| GUI                         | **✅**                                                      | **✅**                                                                        | ❌                                                          | 
| Sniffing                    | ❌                                                          | **✅**                                                                        | **✅**                                                      | 
| Pcap processing             | **✅**                                                      | **✅**                                                                        | **✅**                                                      | 
| Log processing              | **✅**                                                      | ❌                                                                            | **✅**                                                      | 
| Packet decoding             | ❌                                                          | **✅**                                                                        | **✅**                                                      | 
| Filtering                   | **✅**                                                      | **✅**                                                                        | **✅**                                                      | 
| Scripting                   | ❌                                                          | ❌                                                                            | **✅**                                                      | 
| Signature Support           | **✅**                                                      | ❌                                                                            | **✅**                                                      | 
| Statistics                  | **✅**                                                      | **✅**                                                                        | **✅**                                                      | 
| File Extraction             | ❌                                                          | **✅**                                                                        | **✅**                                                      |
| Handling pcaps<br>>over 1GB | Medium performance                                         | Low performance                                                              | Good performance                                           |
| Ease of Management          | 4/5                                                        | 4/5                                                                          | 3/5                                                        |

