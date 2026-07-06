## NIST Incident Response Lifecycle

So this lifecycle is basically the detailed version of detect protect respond and recover from the csf but here it gets split into four phases preparation then detection and analysis then containment eradication and recovery and finally post incident activity. The thing i learned is this is not a straight line its a cycle so steps can loop back and overlap when new stuff gets discovered during response.

## What Actually Counts as an Incident

An event is just anything observable that happens on a system like a password reset request going through. That alone is not a big deal since its logged and its normal. But if a malicious actor is the one who did the password reset without permission then it becomes both an event and a security incident. So basically all incidents are events but not all events are incidents the difference is whether someone violated policy or law to make it happen.

##  The 5 w's

Every incident investigation is basically about figuring out

- who triggered it
- what happened
- when it happened
- where it happened
- why it happened

This info matters not just while responding but later too when writing the final report so you need somewhere to keep track of it as you go.

## Incident Handlers Journal

This is just a notebook basically digital or physical where you log all the incident details as you investigate. Its the main documentation tool analysts use to keep track of the 5 ws while working a case.

## Documentation Types and Tools

Documentation is honestly just any recorded content that helps guide or instruct on something could be audio digital handwritten even video. There is no fixed standard for how a company documents stuff everyone tailors it based on their needs. Common types are

- playbooks
- incident handlers journals
- policies
- plans
- final reports

A playbook works kind of like a product manual it tells you the steps to take for a specific operational action. If documentation is unclear or messy it just creates confusion during a security incident when things are already tense so effective documentation has to be clear consistent and accurate.

Tools used for documenting include word processors like google docs onenote evernote and notepad++ ticketing systems like jira and also google sheets audio recorders cameras and handwritten notes.

## CSIRT

CSIRT stands for computer security incident response team and its basically a specialized group trained specifically in incident management and response. Their goal is to manage incidents efficiently give resources for recovery and try to prevent future incidents. They also work with non security teams like legal hr and pr because for example if pii or financial docs got breached legal has to get involved and pr has to handle public disclosure since some regulations require reporting within a certain time.

Roles inside a csirt

- security analyst investigates alerts and figures out if its really an incident then rates how critical it is small stuff gets handled directly bigger stuff gets escalated
- technical lead takes over the technical side once escalated finds root cause and builds the strategy for containment eradication and recovery
- incident coordinator keeps everything and everyone in sync tracks the response and makes sure other departments stay updated

Some orgs call csirt something else like incident handling team iht or security incident response team sirt and role names can differ too like technical lead being called ops lead but the goal stays the same.

## SOC

Soc is security operations center a dedicated unit that monitors networks systems and devices for threats basically the blue team in action. It can be its own separate team or exist inside a csirt.

Soc analysts are split into tiers

- l1 lowest tier monitors and prioritizes alerts creates and closes tickets escalates when needed
- l2 gets escalated tickets from l1 does deeper investigation and configures security tools reports to lead
- l3 lead handles advanced stuff like malware and forensics analysis manages team reports to manager

Above that is the soc manager who hires trains and evaluates the team creates performance metrics and reports to execs. There are also specialized roles like forensic investigators who preserve and analyze digital evidence and threat hunters who actively hunt down new threats using intel.

## Incident Response Plan

This is a document that lays out the procedures for every step of incident response. Just like teams plans are not identical every org shapes theirs based on mission size culture industry and structure some keep it inside their security plan others keep it separate.

Common elements in a plan

- incident response procedures step by step instructions on how to respond
- system information stuff like network diagrams data flow diagrams logging and asset inventory
- other documents like contact lists forms and templates

Plans are never perfect so they need to be reviewed and tested regularly through tabletop exercises or simulations this also helps find gaps and sometimes its required for regulatory reasons too.

## Security Analyst Toolbox

As an analyst you dont just rely on one tool you use a mix of detection tools documentation tools and investigative tools like packet sniffers. Since threats keep evolving and attackers get sneakier you gotta keep expanding what tools you know.

## IDS and IPS

An ids is like a home intrusion sensor it monitors system and network activity and sends an alert when something abnormal shows up but it doesnt stop anything itself. An ips does everything an ids does but also takes action to actually stop the intrusion kind of like a jewelry store window that automatically rolls down a steel door when it senses the glass breaking. Some tools can do both ids and ips at once popular ones are snort zeek kismet sagan and suricata.

## Detection Categories

While reviewing ids alerts you gotta know these

- true positive alert correctly caught a real attack
- true negative nothing malicious happened and no alert went off which is correct
- false positive alert went off but there was no actual threat wastes time investigating
- false negative a real threat happened but no alert triggered this one is the dangerous one since the team has no idea theyre exposed

## EDR

Edr is endpoint detection and response it gets installed directly on endpoints like laptops phones tablets basically any device on the network. Difference from ids ips is edr does behavioral analysis using ml and ai to catch weird patterns and it can auto block a suspicious process without a human stepping in. Examples are open edr bitdefender endpoint detection and response and fortiedr.

## SIEM

Siem stands for security information and event management its basically the dashboard for the whole network like a cars dashboard warning light telling you when somethings off instead of checking every part yourself. It works in three steps

- collect and aggregate data from firewalls servers routers etc into one centralized place
- normalize data meaning it cleans up the raw logs and puts them into a consistent structured format so its searchable
- analyze data using rule sets and if something matches a rule it triggers an alert for the team correlation also happens here comparing multiple log events to spot patterns

Parsing also happens during collection where raw log lines get split into readable fields and values like host process source ip and source port instead of one messy string.

Some common siem tools are alienvault ossim chronicle elastic exabeam ibm qradar logrhythm and splunk.

## SOAR

Soar is security orchestration automation and response its different from siem because instead of just reporting alerts for a human to review it actually automates the analysis and response part. It can also track and manage cases where multiple related incidents get grouped and viewed together in one place.