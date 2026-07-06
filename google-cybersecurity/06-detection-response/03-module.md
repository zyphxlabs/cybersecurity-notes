## Detection Methods

Detection and analysis phase is basically when security teams get notified of a possible incident and then work to investigate and verify it by collecting and analyzing data. Detection just means catching the security event quickly and analysis means actually digging in to confirm if the alert is real or not. Tools like ids and siem help with this but they only catch what theyre configured to look for so if configuration is off stuff slips through which is why teams need more than just automated tools.

## Threat Hunting

Threat hunting is basically proactively going out and searching for threats instead of waiting for a tool to alert you. Since attackers keep evolving automated detection alone cant keep up so this combines human judgement with tech to catch stuff that slipped past like fileless malware which hides in memory instead of using files so normal signature based detection cant see it. People who do this are called threat hunters and they use threat intel iocs ioas and machine learning together to hunt down probable threats before they cause real damage.

## Threat Intelligence

Threat intelligence is basically evidence based info that gives context about threats that already exist or are emerging. It comes from stuff like

- industry reports which talk about attacker tactics techniques and procedures ttp
- government advisories which are similar just from govt side
- threat data feeds which give live streams of indicators like ip addresses domains and file hashes especially useful against apts which are attackers who stay hidden in a system for a long time

Since this data can pile up fast organizations use a threat intelligence platform tip to centralize and analyze it all in one place. Important thing to remember is this data should add context to detections not fully drive them on its own.

## Cyber Deception And Honeypots

Cyber deception is basically tricking the attacker on purpose to catch them or slow them down. Honeypots are a good example theyre fake systems or files made to look valuable and vulnerable so if an attacker touches it security teams get alerted right away like leaving a fake file named something juicy just to see who bites.

## Ci Cd Pipeline Monitoring

Since ci cd pipelines push code out fast they also open doors for attackers so ongoing monitoring here is important to catch weird stuff early. Common iocs to watch in a pipeline include

- unauthorized code changes like edits from people who shouldnt be touching code or changes at odd hours
- suspicious deployments like deploying straight from a dev branch or at unexpected times
- compromised dependencies like known cves showing up or new unexpected packages getting pulled in
- unusual pipeline execution like steps failing randomly or taking way longer than normal
- attempts to access secrets from places they shouldnt be accessed from

Logs are the backbone for catching all this stuff like pipeline execution logs commit logs access logs and deployment logs and connecting all this to a siem helps automatically flag anomalies at scale using rules and machine learning. Real time alerts also matter here so teams get notified fast instead of finding out after damage is done. Theres also continuous vulnerability scanning which checks the ci cd tools and containers themselves for known weaknesses before attackers can exploit them.

## Ioc Vs Ioa

Ioc is basically evidence of something that already happened like noticing your stuff got stolen from your car after the fact. Ioa on the other hand is about catching the actual behavior in real time like watching someone try to break into the car while its happening. So ioc tells you who and what happened after the fact and ioa tells you the how and why while its still going on. One important thing is iocs arent always proof of an attack sometimes its just human error or a system glitch not related to security at all.

## Pyramid Of Pain

This concept was made by david j bianco and its basically about how much pain an attacker feels when we block different types of indicators. The easier ones to block cause less pain for the attacker since they can just switch it up quickly while the harder ones actually mess up their whole operation. From easiest to hardest to block

- hash values which are unique fingerprints of malicious files
- ip addresses like 192.168.1.1 which attackers can just swap out easily
- domain names like a fake website address
- network artifacts which is stuff visible in network traffic like weird user agent strings
- host artifacts which is evidence left on a device like a strange file created by malware
- tools which is the actual software attackers use like password cracking tools such as john the ripper
- ttps tactics techniques and procedures which is literally their whole behavior pattern and this is the hardest one to block since it means changing their entire approach

## Adding Context With Threat Intel

Just blocking one single ip or file doesnt really solve anything since attackers can just switch tactics so security analysts use threat intelligence to zoom out and build the bigger picture around an ioc instead of looking at it in isolation. This helps teams actually understand the full story of an incident instead of reacting to just one small piece of it.

## Crowdsourcing And Osint

Crowdsourcing is basically pooling knowledge from the wider cybersecurity community instead of every org fighting attacks alone. This is helpful because attackers often reuse the same attack on multiple targets so if one org shares what they found others can defend against it before even getting hit. Isacs are a good example of this they share threat intel specific to industries like healthcare or energy. Osint is basically gathering intel from public sources like websites social media or forums to build a picture of a threat actor or vulnerability.

## Virustotal And Other Tools

Virustotal lets you check files urls domains and ips against multiple antivirus vendors to see if somethings flagged as malicious. The report gives you stuff like

- detection tab shows what each vendor thinks about the artifact
- details tab shows stuff like hashes file size and creation time
- relations tab shows other connected iocs like urls or dropped files
- behavior tab shows what the file actually does when run in a sandbox
- community tab is where people leave comments and insights

Theres also a vendor ratio score and community score at the top and the higher these are the more likely the file is actually malicious. Just remember uploading stuff to virustotal makes it public so dont upload personal or sensitive files.

Other similar tools

- jotti malware scan lets you scan files against multiple antivirus engines for free with some submission limits
- urlscan.io scans and gives a report on suspicious urls
- malwarebazaar is basically a public repository of malware samples used for research

## Documentation Benefits

Documentation gives three main things transparency standardization and clarity. Transparency means theres a clear record of what happened which matters for insurance claims audits and legal stuff chain of custody is a good example of this. Standardization means everyone follows the same set procedure like how an incident response plan lays out steps in advance so response stays consistent no matter who handles it. Clarity means people can quickly understand whats going on and what to do without confusion like playbooks giving clear instructions during a stressful incident.

## Standards And Incident Response Plan

Standards are basically references that guide how policies get set in the first place. An incident response plan is a document that outlines the exact procedures to take during each step of incident response and its a good example of documentation that creates standardization since everyone follows the same steps no matter who ends up responding.

## Documentation Best Practices

- know your audience since a report written for a soc manager will look different than one written for a ceo who might not understand technical jargon
- be concise and put the purpose right at the start so people dont have to dig through a long report to find out whats important
- update documentation regularly since threats and vulnerabilities keep changing so old docs become useless fast

## Chain Of Custody

Chain of custody is basically the paper trail that tracks who touched a piece of evidence when and why during an incident. Like say a hard drive gets pulled for forensic analysis the person handling it first makes sure its write protected so nothing on it can change then they record a hash of the drive so any tampering can be detected later. Every single time the evidence changes hands like from one analyst to another department the transfer gets logged in the chain of custody form. This form usually has stuff like evidence description including things like hostname mac address or ip and a custody log showing who transferred and received it and when and why.

If somewhere along the way an entry gets missed or logged wrong thats called a broken chain of custody and it can seriously mess up whether that evidence is even trustworthy enough to be used in court. So basically the whole point of chain of custody is making sure evidence stays legit from start to finish so it holds up legally.

## Triage Process

Triage is just prioritizing incidents based on how important or urgent they are so teams dont waste time and resources on stuff that doesnt matter as much. It has three steps

- receive and assess where the analyst gets an alert like from an ids and checks if its even legit by asking questions like is this a false positive has this happened before whats the severity
- assign priority where they look at functional impact meaning how much it disrupts business info impact meaning how much sensitive data is exposed and recoverability meaning whether its even worth the effort to fix
- collect and analyze where the analyst gathers evidence does research and documents everything then escalates to level two or a manager if its too complex

Triage helps with resource management so teams focus energy on the real threats and it also gives a standardized process since playbooks guide how alerts move through the pipeline consistently.

## Business Continuity Planning

A bcp is a document that lays out how to keep business operations running during and after a major disruption. Its different from a disaster recovery plan since dr plans are more about recovering systems after something like a natural disaster or hardware failure while bcp is about keeping the business itself functioning. Like if ransomware hits a hospital and locks up patient records that can seriously mess with healthcare delivery so having a bcp helps minimize how much that disruption actually affects critical services.

## Site Resilience

Resilience is just the ability to prepare for handle and bounce back from disruptions. Site resilience specifically is about keeping networks and data centers available even during a disruption and it comes in three types

- hot sites which are fully ready duplicate environments that can be switched on immediately
- warm sites which are mostly ready but need a bit of setup before going fully live
- cold sites which barely have any infrastructure ready so it takes real effort to get operational after a disruption

## Containment Eradication And Recovery

These three steps are all connected containment sets up eradication and eradication sets up recovery. Containment is about stopping the damage from spreading further like isolating an infected computer by cutting it off the network so malware cant jump to other systems. Eradication is about fully removing every trace of the threat like patching the vulnerability that let the attacker in in the first place. Recovery is about bringing affected systems back to normal like reimaging machines resetting passwords or updating firewall rules. Since the whole lifecycle is cyclical teams sometimes gotta loop back to earlier phases if new related incidents pop up.

## Post Incident Activity

This is the final phase and its basically about reviewing everything that happened so the team can improve for next time. A big part of this is the lessons learned meeting also called a post mortem which should happen within two weeks of the incident being resolved. This meeting isnt about blaming anyone even if it turns out someone clicked a phishing link or missed a step its about figuring out what went wrong and how to fix the process. Questions usually asked here are

- what happened
- what time did it happen
- who discovered it
- how did it get contained
- what actions were taken for recovery
- what could have been done differently

## Final Report

The final report is basically the full writeup of everything that happened during the incident and its used as the main reference during the lessons learned meeting. Its not standardized across orgs but usually contains

- executive summary which is the short high level overview for people who dont need all the technical detail
- timeline which lays out everything in chronological order
- investigation section detailing what was analyzed and how
- recommendations which lists out what should change going forward to avoid a repeat

Since business execs and non technical people often read this report its important to keep the language simple where needed instead of drowning them in technical jargon.