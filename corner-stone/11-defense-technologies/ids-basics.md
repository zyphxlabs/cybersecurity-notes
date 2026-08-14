## IDS Fundamentals
Firewall is usually deployed at the boundary of a network and it checks traffic when a connection is about to happen and blocks it if it breaks the rules. But theres always a chance an attacker sneaks past the firewall through something that looks legit and then starts doing malicious stuff once hes inside. Thats where an intrusion detection system or ids comes in, it sits inside the network and detects that activity after it already got past the gate

Its like building security, firewall is the gatekeeper checking people coming in and going out, but if someone slips past the gate the surveillance cameras inside the building are what catch him doing something bad. Ids plays that camera role, it sits and monitors traffic using signature and anomaly based detection and when it finds something abnormal it generates an alert for the admins. Important thing is ids only detects and alerts it doesnt actually block or act on anything

## Deployment Modes
Ids can be deployed in two ways depending on scope

- HIDS host intrusion detection system — installed on individual hosts and only detects threats for that specific host, gives detailed visibility into that hosts activity but gets resource heavy and hard to manage across a large network since you need it on every host
- NIDS network intrusion detection system — monitors traffic across the whole network regardless of specific hosts, gives a centralized view of everything happening network wide

## Detection Modes
Signature based ids keeps a database of known attack patterns called signatures, when the same attack pattern shows up again it gets matched and flagged. The stronger the signature database the better it catches known threats but the downside is it cant catch zero day attacks since those have no existing signature saved anywhere

Anomaly based ids works differently, it first learns the normal baseline behavior of the system or network and then flags anything that deviates from that baseline. This means it can catch zero day attacks since it doesnt rely on signatures at all, but the tradeoff is it tends to generate a lot of false positives because legit programs can sometimes behave in ways that look unusual too. Fine tuning it by manually defining whats normal can help cut down those false positives

Hybrid ids combines both approaches, if a threat already has a known signature it uses signature detection, and if its something new it falls back on anomaly detection. Signature based is fast but can miss new stuff, anomaly and hybrid have more overhead but are better suited for catching the zero day attacks that keep increasing these days

## Snort
Snort is one of the most popular open source ids tools, it came out in 1998 and uses both signature and anomaly based detection through rule files. It comes with a bunch of built in rules that already cover a lot of known attack patterns but you can also write custom rules for traffic that isnt covered by default, or even disable built in rules that dont apply to your setup

## Modes of Snort
Snort can run in three different modes depending on what you need

- Packet sniffer mode — just reads and displays packets without analyzing them, useful for diagnosing network issues rather than actual detection
- Packet logging mode — logs traffic into a pcap file for later analysis, useful for forensic investigations after an attack already happened
- NIDS mode — the main mode, monitors traffic in real time and matches it against rule files to generate alerts, this is basically what gives snort its actual ids functionality

## Rule Format
Snort rules follow a specific structure with a few key components

- Action — what to do when the rule matches, like alert
- Protocol — which protocol the rule applies to, like icmp for ping traffic
- Source ip and port — where the traffic is coming from, can be set to any if you want to catch traffic from anywhere
- Destination ip and port — where the traffic is going to, often set to a defined network range variable
- msg — the message shown when the rule triggers, should describe what was detected
- sid — signature id, a unique identifier for the rule so it can be told apart from others
- rev — revision number, increases every time the rule gets modified so changes can be tracked

So basically a rule combines the action protocol source and destination fields with the metadata in parentheses at the end to define exactly what traffic to catch and how to report it