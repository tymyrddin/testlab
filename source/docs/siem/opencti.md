# OpenCTI

[OpenCTI](https://www.opencti.io/), an open-source threat intelligence platform can use the MITRE ATT&CK framework to structure the data. Additionally, it can be integrated with other threat intel tools such as [MISP](misp.md) and [TheHive](thehive.md). 

## OpenCTI Dashboard

| ![OpenCTI architecture](../../_static/images/opencti.png) |
|:--:|
| The opening dashboard shows visual widgets summarising the threat data ingested into OpenCTI. |

The OpenCTI categorises and presents entities under the Activities and Knowledge groups on the left-side panel.

* The activities section covers security incidents ingested onto the platform in the form of reports. It makes it easy for 
analysts to investigate these incidents. 
* The Analysis tab contains the input entities in reports analysed and associated external references. Reports are 
central to OpenCTI as knowledge on threats and events are extracted and processed. They allow for easier identification 
of the source of information by analysts. Additionally, analysts can add their investigation notes and other external 
resources for knowledge enrichment. 
* Security analysts investigate and hunt for events involving suspicious and malicious activities across their 
organisational network. Within the Events tab, analysts can record their findings and enrich their threat intel by 
creating associations for their incidents.
* Technical elements, detection rules and artefacts identified during a cyberattack are listed under this tab: one or 
several identifiable makeup indicators. These elements assist analysts in mapping out threat events during a hunt and 
perform correlations between what they observe in their environments against the intel feeds.

The Knowledge section provides linked data related to the tools adversaries use, targeted victims and the type of 
threat actors and campaigns used.

### Threats

All information classified as threatening to an organisation or information would be classified under threats:

* Threat Actors: An individual or group of attackers seeking to propagate malicious actions against a target.
* Intrusion Sets: An array of TTPs, tools, malware and infrastructure used by a threat actor against targets who 
share some attributes. APTs and threat groups are listed under this category on the platform due to their known 
pattern of actions.
* Campaigns: Series of attacks taking place within a given period and against specific victims initiated by advanced 
persistent threat actors who employ various TTPs. Campaigns usually have specified objectives and are orchestrated 
by threat actors from a nation state, crime syndicate or other disreputable organisation.

### Arsenal

The tab lists all items related to an attack and any legitimate tools identified from the entities.

* Malware: Known and active malware and trojan are listed with details of their identification and mapping based on 
the knowledge ingested into the platform. For example, we can analyse the 4H RAT malware, and extract information and 
associations made about the malware.

| ![OpenCTI arsenal 4H RAT](../../_static/images/opencti-arsenal.png) |
|:--:|
| Putter Panda |

* Attack Patterns: Adversaries implement and use different TTPs to target, compromise, and achieve their objectives. 
We can look at the details of the Command-Line Interface and make decisions based on the relationships established on 
the platform and navigate through an investigation associated with the technique.

| ![OpenCTI arsenal attack pattern Command-Line Interface](../../_static/images/opencti-arsenal2.png) |
|:--:|
| Kill chain phase `execution-ics` |

* Courses of Action: MITRE maps out concepts and technologies that can be used to prevent an attack technique from 
being employed successfully. These are represented as Courses of Action (CoA) against the TTPs.
* Tools: Lists all legitimate tools and services developed for network maintenance, monitoring and management. 
Adversaries may also use these tools to achieve their objectives. For example, for the Command-Line Interface attack 
pattern, it is possible to narrow down that CMD would be used as an execution tool. As an analyst, one can 
investigate reports and instances associated with the use of the tool.
* Vulnerabilities: Known software bugs, system weaknesses and exposures are listed to provide enrichment for what 
attackers may use to exploit and gain access to systems. The Common Vulnerabilities and Exposures (CVE) list 
maintained by MITRE is used and imported via a connector.

### Entities

This tab categorises all entities based on operational sectors, countries, organisations and individuals. This 
information allows for knowledge enrichment on attacks, organisations or intrusion sets.

### General tabs navigation

The day-to-day usage of OpenCTI would involve navigating through different entities within the platform to understand 
and use the information for any threat analysis. 

A walkthrough for the Cobalt Strike malware entity:

Overview Tab: Provides the general information about an entity being analysed and investigated:

| ![OpenCTI Cobalt Strike Overview](../../_static/images/opencti-cobalt.png) |
|:--:|
| Entity ID, confidence level, description, relations created based on threats, intrusion sets and <br>attack patterns, reports mentioning the entity and any external references. |

Knowledge Tab: Presents linked information associated with the entity selected:

| ![OpenCTI Cobalt Strike Knowledge](../../_static/images/opencti-cobalt2.png) |
|:--:|
| Associated reports, indicators, relations and attack pattern timeline of the entity. |

Additionally, an analyst can view fine-tuned details from the tabs on the right-hand pane, where information about 
the threats, attack vectors, events and observables used within the entity are presented.

Analysis Tab: Provides the reports where the identified entry has been seen. 

|       ![OpenCTI Cobalt Strike Analysis](../../_static/images/opencti-cobalt3.png)       |
|:---------------------------------------------------------------------------------------:|
| The analysis provides usable information about a threat and guides investigation tasks. |

Indicators Tab: Provides information on IOC identified for all the threats and entities.

Data Tab: Contains the files uploaded or generated for export that are related to the entity. These assist in 
communicating information about threats being investigated in either technical or non-technical formats.

History Tab: Changes made to the element, attributes, and relations are tracked by the platform worker and this tab 
will outline the changes.

OpenCTI uses a variety of knowledge schemas in structuring data, the main one being the Structured Threat Information 
Expression (STIX2) standards. STIX is a serialised and standardised language format used in threat intelligence 
exchange. It allows for the data to be implemented as entities and relationships, effectively tracing the origin of 
the provided information.

| ![OpenCTI architecture](../../_static/images/opencti-arch.png) |
|:--------------------------------------------------------------:|
|  The data model is supported by the platform's architecture.   |

## Data model

### Services

* GraphQL API: The API connects clients to the database and the messaging system.
* Write workers: Python processes utilised to write queries asynchronously from the RabbitMQ messaging system.
* Connectors: Another set of python processes used to ingest, enrich or export data on the platform. These connectors 
provide the application with a network of integrated systems and frameworks to create threat intelligence relations 
and allow users to improve their defence tactics.

### Connectors

| Class                          | Description                                                  | Examples                  |
|:-------------------------------|:-------------------------------------------------------------|:--------------------------|
| External Input Connector       | Ingests information from external sources                    | CVE, MISP, TheHive, MITRE |
| Stream Connector               | Consumes platform data stream                                | History, Tanium           |
| Internal Enrichment Connector  | Takes in new OpenCTI entities from user requests             | Observables enrichment    |
| Internal Import File Connector | Extracts information from uploaded reports                   | PDFs, STIX2 Import        |
| Internal Export File Connector | Exports information from OpenCTI into different file formats | CSV, STIX2 export, PDF    |

## Resources

* [We are Filigran, the new home for OpenCTI and OpenEx](https://medium.com/filigran/we-are-filigran-the-new-home-for-opencti-and-openex-b613ba9c7f99)
* [Filigran](https://www.filigran.io/en/)
