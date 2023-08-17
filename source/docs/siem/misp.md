# MISP

[MISP](https://www.misp-project.org/) (Malware Information Sharing Platform) is an open-source threat information platform that facilitates the collection, storage and distribution of threat intelligence and Indicators of Compromise (IOCs) related to malware, cyberattacks, financial fraud or any intelligence within a community of trusted members. 

## Dashboard

MISP is effectively useful for the following use cases:

* Malware Reverse Engineering: Sharing of malware indicators to understand how different malware families function.
* Security Investigations: Searching, validating and using indicators in investigating security breaches.
* Intelligence Analysis: Gathering information about adversary groups and their capabilities.
* Law Enforcement: Using indicators to support forensic investigations.
* Risk Analysis: Researching new threats, their likelihood and occurrences.
* Fraud Analysis: Sharing of financial indicators to detect financial fraud.

### Dashboard

The analyst's view of MISP provides you with the functionalities to track, share and correlate events and IOCs identified during your investigation. The dashboard's menu contains the following options, and we shall look into them further:

* Home button: Returns you to the application's start screen, the event index page or the page set as a custom home page using the star in the top bar.
* Event Actions: All the malware data entered into MISP comprises an event object described by its connected attributes. The Event actions menu gives access to all the functionality related to the creation, modification, deletion, publishing, searching and listing of events and attributes.
* Dashboard: This allows you to create a custom dashboard using widgets.
* Galaxies: Shortcut to the list of MISP Galaxies on the MISP instance. More on these on the Feeds & Taxonomies Task.
* Input Filters: Input filters alter how users enter data into this instance. Apart from the basic validation of attribute entry by type, the site administrators can define regular expression replacements and blocklists for specific values and block certain values from being exportable. Users can view these replacement and blocklist rules here, while an administrator can alter them.
* Global Actions: Access to information about MISP and this instance. You can view and edit your profile, view the manual, read the news or the terms of use again, see a list of the active organisations on this instance and a histogram of their contributions by an attribute type.
* MISP: Simple link to your baseurl.
* Name: Name (Auto-generated from Mail address) of currently logged in user.
* Envelope: Link to User Dashboard to consult some of your notifications and changes since the last visit. Like some of the proposals received for your organisation.
* Log out: The Log out button to end your session immediately.

### Event management

The Event Actions tab is where you, as an analyst, will create all malware investigation correlations by providing descriptions and attributes associated with the investigation. Splitting the process into three significant phases, we have: 

* Event Creation.
* Populating events with attributes and attachments.
* Publishing.

### Event creation

In the beginning, events are a storage of general information about an incident or investigation. We add the description, time, and risk level deemed appropriate for the incident by clicking the Add Event button. Additionally, we specify the distribution level we would like our event to have on the MISP network and community. According to MISP, the following distribution options are available:

* Your organisation only: This only allows members of your organisation to see the event.
* This Community-only: Users that are part of your MISP community will be able to see the event. This includes your organisation, organisations on this MISP server and organisations running MISP servers that synchronise with this server.
* Connected communities: Users who are part of your MISP community will see the event, including all organisations on this MISP server, all organisations on MISP servers synchronising with this server, and the hosting organisations of servers that are two hops away from this one.
* All communities: This will share the event with all MISP communities, allowing the event to be freely propagated from one server to the next.

### Attributes & attachments

Attributes can be added manually or imported through other formats such as OpenIOC and ThreatConnect. To add them manually, click the Add Attribute and populate the form fields.

Some essential options to note are: 

* For Intrusion Detection System: This allows the attribute to be used as an IDS signature when exporting the NIDS data unless it overrides the permitted list. If not set, the attribute is considered contextual information and not used for automatic detection.
* Batch import: If there are several attributes of the same type to enter (such as a list of IP addresses, it is possible to join them all into the same value field, separated by a line break between each line. This will allow the system to create separate lines for each attribute.

### Publish event

Once the analysts have created events, the organisation admin will review and publish those events to add them to the pool of events. This will also share the events to the distribution channels set during the creation of the events.

## Feeds

Feeds are resources that contain indicators that can be imported into MISP and provide attributed information about security events. These feeds provide analysts and organisations with continuously updated information on threats and adversaries and aid in their proactive defence against attacks.

MISP Feeds provide a way to:

* Exchange threat information.
* Preview events along with associated attributes and objects.
* Select and import events to your instance.
* Correlate attributes identified between events and feeds.

Feeds are enabled and managed by the Site Admin for the analysts to obtain information on events and indicators. 

## Taxonomies

A taxonomy is a means of classifying information based on standard features or attributes. On MISP, taxonomies are used to categorise events, indicators and threat actors based on tags that identify them.

Analysts can use taxonomies to:

* Set events for further processing by external tools such as VirusTotal.
* Ensure events are classified appropriately before the Organisation Admin publishes them.
* Enrich intrusion detection systems' export values with tags that fit specific deployments.

Taxonomies are expressed in machine tags:

* Namespace: Defines the tag's property to be used.
* Predicate: Specifies the property attached to the data.
* Value: Numerical or text details to map the property.

Taxonomies are listed under the Event Actions tab. The site admin can enable relevant taxonomies.

## Tagging

Information from feeds and taxonomies, tags can be placed on events and attributes to identify them based on the indicators or threats identified correctly. Tagging allows for effective sharing of threat information between users, communities and other organisations using MISP to identify various threats.

Tags can be added by clicking on the buttons in the Tags section and searching from the available options appropriate to the case. The buttons represent global tags and local tags, respectively. It is also important to note that you can add your unique tags to your MISP instance as an analyst or organisation that would allow you to ingest, navigate through and share information quickly within the organisation.

### Tagging at event level vs attribute level

Tags can be added to an event and attributes. Tags are also inheritable when set. It is recommended to set tags on the entire event and only include tags on attributes when they are an exception from what the event indicates. This will provide a more fine-grained analysis.

### The minimal subset of tags

The following tags can be considered a must-have to provide a well-defined event for distribution:

* [Traffic Light Protocol](https://www.first.org/tlp/): Provides a colour schema to guide how intelligence can be shared.
* Confidence: Provides an indication whether the data being shared is of high quality and has been vetted so that it can be trusted to be good for immediate usage.
* Origin: Describes the source of information and whether it was from automation or manual investigation.
* Permissible Actions Protocol: An advanced classification that indicates how the data can be used to search for compromises within the organisation.

## Resources

* [MISP Install - 1 Million (+) Free IoCs](https://www.youtube.com/watch?v=Etr9vVC6WYQ&list=PLB6hQ_WpB6U0WeroZAfssgRpxW8olnkqy&index=12)
* [Wazuh + MISP Automation - Automate Your SIEM Threat Intel](https://www.youtube.com/watch?v=I53HNekwu7w&list=PLB6hQ_WpB6U0WeroZAfssgRpxW8olnkqy&index=14)
* [MISP Book](https://www.circl.lu/doc/misp/)
* [MISP GitHub](https://github.com/MISP/)
* [CIRCL MISP Training Module 1](https://www.youtube.com/watch?v=aM7czPsQyaI)
* [CIRCL MISP Training Module 2](https://www.youtube.com/watch?v=Jqp8CVHtNVk)
