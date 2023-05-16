# Zeek

Zeek (formerly Bro) is an open-source and commercial passive Network Monitoring tool (traffic analysis framework) 
developed by Lawrence Berkeley Labs. Today, Zeek is supported by several developers, and Corelight provides an 
Enterprise-ready fork of Zeek. Therefor this tool is called both open source and commercial. The differences between 
the open-source version and the commercial version are detailed [here](https://corelight.com/products/compare-to-open-source-zeek?hsLang=en).

Zeek differs from known monitoring and IDS/IPS tools by providing a wide range of detailed logs ready to investigate 
both for forensics and data analysis actions. Currently, Zeek provides 50+ logs in 7 categories.

## Differences between Snort and Zeek

While both are called IDS/NIDS, it is good to know the cons and pros of each tool and use them in a specific manner. 
There are some overlapping functionalities, but they are different in purpose.


| **Tool**                 | **Zeek**                                                                                                                                                                                        | **Snort**                                                                                                                                                             |
|:-------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Capabilities**         | NSM and IDS framework. <br>Heavily focused on network analysis, <br>on specific threats to trigger alerts, <br>and the detection mechanism is  <br>focused on events.                           | An IDS/IPS system. <br>Heavily focused on signatures to <br>detect vulnerabilities, and the <br>detection mechanism is focused on <br>signature patterns and packets. |
| **Pros**                 | Hard to use. <br>The analysis is done out of the Zeek, <br>manually or by automation.                                                                                                           | Hard to detect complex threats.                                                                                                                                       |
| **Cons**                 | Provides in-depth traffic visibility. <br>Useful for threat hunting. <br>Ability to detect complex threats. <br>Has a scripting language <br>Supports event correlation. <br>Easy to read logs. | Easy to write rules. <br>Cisco supported rules. <br>Community support.                                                                                                |
| **Common <br>use cases** | Network monitoring. <br>In-depth traffic investigation. <br>Intrusion detecting in chained events.                                                                                              | Intrusion detection and prevention. <br>Stop known attacks/threats.                                                                                                   |

## Zeek architecture

| ![Zeek](../../_static/images/zeek-arch.png)
|:--:|
| Zeek has two primary layers: an `Event Engine` and a `Policy Script Interpreter`.  |

The Event Engine layer is where the packets are processed; it is called the event core and is responsible for 
describing the event without focusing on event details. It is where the packages are divided into parts such as source 
and destination addresses, protocol identification, session analysis and file extraction. The Policy Script Interpreter 
layer is where the semantic analysis is conducted. It is responsible for describing the event correlations by using 
Zeek scripts.

## Zeek frameworks

Zeek has several frameworks to provide extended functionality in the scripting layer. These frameworks enhance Zeek's 
flexibility and compatibility with other network components. Each framework focuses on the specific use case and easily 
runs with Zeek installation. For instance, we will be using the "Logging Framework" for all cases. Having ide on each 
framework's functionality can help users quickly identify an event of interest. More on its frameworks 
[here](https://docs.zeek.org/en/master/frameworks/index.html).
