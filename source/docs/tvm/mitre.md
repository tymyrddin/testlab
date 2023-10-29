# MiTRE

Mitre are resources the US-based non-profit MITRE Corporation has created for the cybersecurity community to enhance intrusion detection and prevention, threat hunting, security engineering, etc.

## ATT&CK® framework

The [ATT&CK® (Adversarial Tactics, Techniques, and Common Knowledge) framework](https://attack.mitre.org/) is a 
globally-accessible knowledge base of adversary tactics and techniques based on real-world observations. The ATT&CK 
knowledge base is used as a foundation for the development of specific threat models and methodologies in the private 
sector, in government, and in the cybersecurity product and service community.

In 2013, MITRE began to address the need to record and document common TTPs (Tactics, Techniques, and Procedures) that 
APT (Advanced Persistent Threat) groups used against enterprise Windows networks. This started with an internal project 
known as FMX (Fort Meade Experiment). Within this project, selected security professionals were tasked to emulated 
adversarial TTPs against a network, and data was collected from the attacks on this network. The gathered data helped 
construct the beginning pieces of what we know today as the ATT&CK® framework.

The ATT&CK® framework has grown and expanded throughout the years. One notable expansion was that the framework 
focused solely on the Windows platform but has expanded to cover other platforms, such as macOS and Linux. The 
framework is heavily contributed to by many sources, such as security researchers and threat intelligence reports. 
Note this is not only a tool for blue teamers. The tool is also useful for red teamers.

The ATT&CK Matrix can be used to map a threat group to their tactics and techniques. There are several methods the 
search can be initiated.

### ATT&CK® Matrix

1. Goto to the bottom of the page to view the ATT&CK® Matrix for Enterprise. Across the top of the matrix, there are 14 
categories. Each category contains the techniques an adversary could use to perform the tactic. The categories cover 
the seven-stage Cyber Attack Lifecycle (Lockheed Martin Cyber Kill Chain).
2. Under Initial Access, there are 9 techniques. Some techniques have sub-techniques, such as Phishing.
3. Click on the gray bar to the right to view the sub-techniques.
4. Click on the technique or sub-technique.

### ATT&CK® Navigator

The same data can be viewed via the ATT&CK® Navigator: 

_"The ATT&CK® Navigator is designed to provide basic navigation and annotation of ATT&CK® matrices, something that people are already doing today in tools like Excel. We've designed it to be simple and generic - you can use the Navigator to visualize your defensive coverage, your red/blue team planning, the frequency of detected techniques, or anything else you want to do."_

1. Access the Navigator view when visiting a group or tool page.
2. In the sub-menu select view.

## CAR knowledge base

The [CAR (Cyber Analytics Repository) knowledge base](https://car.mitre.org/) is _"a knowledge base of analytics developed by MITRE based on the MITRE ATT&CK® adversary model. CAR defines a data model that is leveraged in its pseudocode representations but also includes implementations directly targeted at specific tools (e.g., Splunk, EQL) in its analytics. With respect to coverage, CAR is focused on providing a set of validated and well-explained analytics, in particular regarding operating theory and rationale."_

### CAR ATT&CK® Navigator layer

The [ATTACK Navigator](https://mitre-attack.github.io/attack-navigator/), the web-based tool for annotating and 
exploring ATT&CK matrices can be used to visualize defensive coverage, red/blue team planning, the frequency of 
detected techniques, etc. It has a CAR ATT&CK® Navigator layer.

## ENGAGE

_"[MITRE Engage](https://engage.mitre.org/) is a framework for planning and discussing adversary engagement operations that empowers you to engage your adversaries and achieve your cybersecurity goals."_

MITRE Engage is considered an Adversary Engagement Approach. This is accomplished by the implementation of Cyber 
Denial and Cyber Deception. With Cyber Denial we prevent the adversary's ability to conduct their operations and with Cyber Deception we 
intentionally plant artifacts to mislead the adversary. 

The Engage website provides a [starter kit](https://engage.mitre.org/starter-kit/) to get you 'started' with the 
Adversary Engagement Approach. The starter kit is a collection of whitepapers and PDFs explaining various checklists, 
methodologies, and processes to get you started. 

### Categories

Categories based on the information on the Engage website.

* Prepare the set of operational actions that will lead to your desired outcome (input)
* Expose adversaries when they trigger your deployed deception activities 
* Affect adversaries by performing actions that will have a negative impact on their operations
* Elicit information by observing the adversary and learn more about their modus operandi (TTPs)
* Understand the outcomes of the operational actions (output)

## D3FEND

D3FEND (Detection, Denial, and Disruption Framework Empowering Network Defence) is a _knowledge graph of cybersecurity countermeasures."_

It is still in beta and is funded by the Cybersecurity Directorate of the NSA and provides information on what is the technique (definition), how the technique works (how it works), things to think about when implementing the technique (considerations), and how to use the technique (example).

As with other MITRE resources, you can filter based on the ATT&CK matrix.

## ENGENUITY

Under [MITRE ENGENUITY](https://mitre-engenuity.org/), we have: 

* [The Center for Threat-Informed Defense](https://mitre-engenuity.org/cybersecurity/ctid/)
* [Attack Evaluations](https://mitre-engenuity.org/cybersecurity/attackevaluations/)
* [MITRE ATT&CK Defender](https://mitre-engenuity.org/cybersecurity/mad/)

## Resources

* [Engage Handbook](https://engage.mitre.org/wp-content/uploads/2022/04/EngageHandbook-v1.0.pdf)
* [Engage Matrix Explorer](https://engage.mitre.org/matrix)
* [Introducing the all-new Adversary Emulation Plan Library](https://medium.com/mitre-engenuity/introducing-the-all-new-adversary-emulation-plan-library-234b1d543f6b), ATT&CK® Emulation Plans
