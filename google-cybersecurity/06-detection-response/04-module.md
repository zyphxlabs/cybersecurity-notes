## Logs Basics

A log is basically a record of stuff that happens inside an organizations systems like a device logging what action happened and who did it. Every log entry usually has stuff like date time location the action and who performed it. Logs used to be just for troubleshooting like figuring out why an app crashed but now they matter a ton for security monitoring too since they help build the full story of what happened during an incident.

## Log Analysis

Log analysis is basically going through logs to spot events that actually matter for an investigation. Since logs come from tons of different sources the volume can get massive fast so its important to be picky about what actually needs logging instead of dumping everything since too much data just slows searches down and makes it harder to find the real issue.

## Types Of Log Sources

- network logs come from stuff like routers switches and firewalls
- system logs come from the operating system itself like windows or linux
- application logs come from software like a smartphone app
- security logs come from tools like ids or antivirus and usually contain stuff like file deletions
- authentication logs record login attempts whether successful or failed

## Log Details Example

Most logs contain a date time location action and who performed it. Like a normal login log might just say something simple like login event at a certain time saying user1 authenticated successfully. But if you turn on verbose logging it records way more detail like the exact device name and ip address the login came from. Verbose is useful when you need more context but it also means more data to store and search through.

## Log Management

Since basically every device produces logs it gets overwhelming fast so log management is about figuring out what to collect how to store it and when to get rid of it. Choosing what to log matters a lot because not every log source is useful for every situation and some data like phone numbers emails or names count as pii which needs special careful handling and sometimes cant even be logged depending on the region.

## Overlogging Problem

Its tempting to just log everything for safety but thats actually the most common mistake orgs make. Logging too much increases storage costs slows systems down and makes searching a nightmare since youre digging through a mountain of irrelevant stuff just to find the one thing that matters.

## Log Retention And Protection

Some industries are required by law to keep logs for a certain period like

- fisma for public sector
- hipaa for healthcare
- pci dss glba and sox for financial services

Protecting logs matters too since attackers sometimes try to edit or delete logs to hide their tracks. Storing logs on a centralized separate server instead of the local machine helps protect their integrity since it puts a barrier between the attacker and the actual log data.

## Log Formats

Logs come in different formats depending on the source some are made to be read by humans and some by machines.

- syslog is both a protocol and a format it transports logs using port 514 for plaintext and 6514 for encrypted and its format has three parts a header structured data and a message the header holds stuff like timestamp hostname and message id
- json uses key value pairs wrapped in curly brackets for objects and square brackets for arrays its lightweight and easy to read which is why its common in web and cloud stuff
- xml uses tags with a start and end tag and can have attributes for extra info its the native format mostly used in windows systems
- csv just separates values with commas and the meaning of each value depends on its position since the field names might not even be shown
- cef structures data using pipes to separate fields like version vendor product severity and then key value pairs for the extension part its often carried over syslog which is why a timestamp and hostname get added in front

## Hids And Nids

A hids is installed directly on a single device like a laptop or server and it watches everything happening locally like unauthorized app installs or weird user activity then it logs and alerts if something looks wrong. A nids on the other hand sits at a point in the network and watches all the traffic passing through instead of just one device so if it spots malicious traffic it logs and alerts too. Using both together basically gives a fuller picture since one watches individual machines and the other watches the whole network.

## Detection Techniques

- signature based analysis compares activity against known patterns called signatures its pretty accurate for known threats so it has fewer false positives but the downside is attackers can slightly tweak their methods to dodge the signature and it also cant catch brand new unknown threats like zero days which are exploits nobody knew about before
- anomaly based analysis first builds a baseline of normal behavior then flags anything that deviates from it this can catch new unknown threats but it also causes more false positives since anything unusual even harmless stuff can get flagged and if an attacker was already active during the baseline training period their bad behavior might accidentally get counted as normal

## Reading Signatures

A signature in an ids basically has three parts action header and rule options. The action comes first and tells the ids what to do if the rule matches like alert pass or reject. The header defines the actual traffic details like source ip destination ip ports protocol and direction so for example specifying tcp traffic from one ip going to another ip on port 80. The rule options let you fine tune the signature further using stuff separated by semicolons inside parentheses like msg which is the alert message sid which is a unique signature id and rev which tracks the revision number every time the signature gets updated.

## Suricata Signatures

Suricata is an open source ids ips and network analysis tool that comes preloaded with rule templates you can use or customize. Looking at an actual suricata rule file lines starting with a pound sign are just comments meant for humans and get ignored by suricata itself. A real signature would specify something like alert as the action then http as protocol with home_net as source going out to external_net which basically means it watches for http traffic leaving the home network. Rule options like msg flow and content help narrow it down further like matching the exact text get inside a packet to catch something like a request being made.

## Eve Json Logs In Suricata

Suricata outputs its logs in eve json format where eve stands for extensible event format. There are two types of logs it produces alert logs and network telemetry logs. Alert logs come from triggered signatures and contain details relevant to a security investigation like the ip addresses protocol and details about which signature triggered including its message and id. Telemetry logs on the other hand just record general network activity like an http connection showing stuff like hostname user agent and content type even if its not necessarily malicious. Both together help build the full picture during an investigation.

## Telemetry

Telemetry is basically the collection and transmission of data for analysis while logs record the actual events themselves. Like a packet capture is a form of network telemetry since it captures raw network activity not just a summarized event entry.

## Siem Process Recap

Siem basically works in three steps collect and process data from tons of sources normalize it into a consistent format and then index it so it can be searched fast. This makes it way easier for analysts to quickly dig through massive amounts of security data without manually checking every device.

## Log Ingestion

Log ingestion is basically the process of pulling in and importing log data from different sources into a siem. When the siem ingests a log it actually makes a copy of it so the original source log stays untouched. Manually uploading logs one by one would be way too slow for a large environment so most orgs use log forwarders which are software that automatically collect and send logs to wherever theyre configured to like a siem. Some operating systems already come with native forwarders and if not you gotta install a third party one.

## Splunk Searching

Splunk uses its own query language called spl search processing language. A basic search like index=main fail tells splunk to look inside the main index for anything containing the word fail. You can also use pipes which is the same idea as piping in linux where the output of one command feeds into the next like index=main fail| chart count by host which takes the failed events and organizes them into a chart based on host. Wildcards using the asterisk symbol help expand searches so fail* would match failed failure and other variations. Using double quotes lets you search for an exact phrase instead of separate words being matched individually.

## Chronicle Searching

Chronicle also known as google secops lets you search using two methods udm search and raw log search. Udm stands for unified data model and its the default search method which searches through normalized structured data so its faster. A basic udm search looks like metadata.event_type = user_login and security_result.action = block which basically finds failed login attempts. Udm events always have common fields like entities which describe the device user or process involved event metadata which describes basic event info network metadata for network related stuff and security results which show the outcome like a virus getting quarantined. Raw log search on the other hand searches through unparsed logs which is slower but useful if the info youre looking for wasnt included in the normalized data it also supports regex for pattern matching.

## Yara L

Chronicle uses a language called yara l to write detection rules for scanning through ingested log data like writing a rule specifically to catch signs of data exfiltration.

## Wazuh

Wazuh is basically a free open source siem alternative to stuff like splunk or chronicle which is helpful since those tools often restrict free access to business emails only. Wazuh lets you do the same core stuff like log analysis threat detection and incident investigation but on a system you fully control. Setting it up involves running it as a virtual machine through virtualbox configuring memory settings setting up a shared folder for data and then using filebeat to ingest logs into the dashboard where you can then search and analyze them just like any other siem.