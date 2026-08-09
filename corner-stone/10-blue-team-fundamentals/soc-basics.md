## Why SOC Exists
Tech made everything faster and easier but that also means theres way more to protect now. Critical data isnt locked in a filing cabinet anymore, its sitting inside networks and systems, and organizations are basically carrying huge amounts of confidential info across all of that. If that data gets disrupted lost or messed with in any way it can cause serious damage. Attackers are out there finding new vulnerabilities in these systems constantly, and honestly just relying on old school security practices isnt enough anymore, you need a whole team dedicated to watching over this stuff

Thats basically what a soc or security operations center is, a dedicated team that continuously monitors an orgs network and resources looking for suspicious activity before it turns into real damage. This team runs 24/7 since threats dont exactly wait for business hours

## Detection and Response
The whole point of a soc team is keeping detection and response tight. They use security solutions that pull the entire companys network and systems into one centralized place so everything can actually be monitored properly instead of piecemeal

On the detection side theres a few different things theyre watching for

- vulnerabilities — a weakness in some device or software that an attacker could exploit to do more than theyre supposed to be able to, like a batch of windows machines that need patching against something already public. Technically fixing these isnt always the socs direct job but unpatched stuff still drags down the whole companys security posture
- unauthorized activity — say an attacker gets ahold of someones username and password and logs in as them, catching this fast before real damage happens matters a lot, stuff like unusual geographic login location is a common clue here
- policy violations — every company has its own security policy defining rules and procedures, and what counts as a violation varies, could be something like downloading pirated stuff on a work machine or sending confidential files over some insecure channel
- intrusions — actual unauthorized access to systems or networks, like someone successfully exploiting a web app or a user getting infected after visiting a shady site

On the response side the soc supports the actual incident response process once somethings been confirmed as a real threat, helping minimize the damage and figure out the root cause alongside the incident response team

## The Three Pillars
A soc becomes actually mature and effective through three pillars working together, people process and technology. None of these alone makes a good soc, its professionals working with proper processes on solid tools that actually gets you somewhere

## People
No matter how automated security tooling gets, people are still the core of a soc. Security solutions alone throw off a ton of alerts and a lot of that ends up being noise. Kinda like imagining a fire department with one centralized system pulling in every fire alarm across a whole city, if a ton of alarms go off at once and it turns out most were just triggered by someone burning toast, all that response effort ends up wasted. Without people actually reviewing and filtering that noise a soc just ends up chasing irrelevant stuff constantly, people are what actually separate real threats from false alarms and drive an appropriate response

The soc team typically breaks down into a few roles

- level 1 analyst — first responders, anything the security tooling flags comes to them first, they do the initial triage to figure out if somethings actually harmful and escalate through proper channels if it is
- level 2 analyst — takes over when something needs deeper digging, correlating data across multiple sources to build out a fuller picture than level 1 alone can
- level 3 analyst — experienced folks who proactively hunt for threat indicators instead of just reacting, and they lead the heavier incident response work like containment eradication and recovery once somethings confirmed serious
- security engineer — handles deploying and configuring the actual security tools everyone else relies on day to day
- detection engineer — builds out the actual detection logic and rules that power the tooling, sometimes this is a dedicated role and sometimes level 2/3 analysts handle it themselves
- soc manager — oversees the processes the team follows and stays in contact with the ciso to report on the teams current posture and ongoing efforts

Worth noting these roles arent fixed, smaller orgs might combine several of these into fewer people while bigger ones split it out even further

## Process
Every role has its own process tied to it, and one of the most important ones is alert triage. This is the first response step for literally any alert that comes in, and its all about figuring out severity and priority by answering the 5 ws

Say an alert comes in for malware detected on some host. Working through the 5 ws on that would look something like

- what — a malicious file got detected on a host inside the network
- when — figuring out the exact time and date it was flagged
- where — which specific host and directory it showed up in
- who — which user account it was tied to
- why — digging into the actual root cause, like finding out the file came from a pirated software site because the user wanted a free version of something

Once somethings confirmed harmful it needs to get escalated properly, usually as a ticket assigned to whoever handles it next. A good report covers all 5 ws with proper analysis and screenshots as actual evidence backing it up

Sometimes what gets reported turns out to be seriously critical, and thats when a full incident response process kicks off, sometimes with dedicated forensics work involved too, digging through system or network artifacts to nail down the actual root cause of what happened

## Technology
People and process alone still need actual tooling behind them to make detection and response realistically possible at scale. A network is made up of tons of devices and apps, and trying to manually watch each one individually would eat up way more time and resources than any team actually has. Security solutions centralize all that info and automate a huge chunk of detection and response

Some of the core tools involved

- siem — security information and event management, pulls in logs from tons of different sources across the network. Detection rules get configured inside it to flag suspicious activity, and it correlates data across multiple log sources to surface real detections. Modern siems go beyond just rule based stuff too, adding user behavior analytics and threat intel often backed by machine learning. Worth remembering siem itself only really covers the detection side, not response
- edr — endpoint detection and response, gives real time and historical visibility specifically at the device level and can actually carry out automated responses too, not just detection. Lets you investigate an endpoint deeply and respond quickly without needing to touch the machine manually
- firewall — purely network focused, sits as a barrier between internal and external networks watching traffic in both directions and filtering out anything unauthorized. Also has its own detection rules to catch and block suspicious traffic before it ever reaches the internal network

Beyond these three theres a bunch of other tools that play their own roles too like antivirus epp ids/ips xdr and soar, what actually gets deployed depends heavily on the orgs specific threat surface and what resources they actually have available

## Practical Walkthrough Notes
Worked through a scenario as a level 1 analyst, an alert came in about port scanning activity detected on one of the hosts in the network, with access to a siem showing all the related logs for it. Task was going through those logs individually and answering the 5 ws for it

Turned out the vulnerability assessment team had actually notified the soc beforehand that they were running an internal port scan from a specific host as part of legit testing, which is a good reminder that not every detection is malicious, sometimes its authorized internal activity that just needs to be verified and documented properly rather than escalated as a real incident