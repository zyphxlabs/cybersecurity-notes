## Playbooks

A playbook is basically a manual that tells you exactly what to do when something goes wrong, step by step. The whole point is that when a security incident happens things move fast and you can't be sitting there figuring out what to do next, so the playbook handles that. It makes sure everyone follows the same consistent process regardless of who's on the case that day. There are different types — incident response playbooks, security alert playbooks, team-specific and product-specific ones — but the most common one you'll deal with as an entry level analyst is the incident response playbook.

Playbooks are also considered living documents meaning the security team keeps updating them constantly as new threats show up, laws change, or they find gaps in the current process. Updates happen when there's a failure found in the procedures, when compliance requirements change, or when threat actors start doing new things the old playbook didn't account for.

## Incident Response Playbook — 6 Phases

The incident response playbook has six phases that take you from start to finish when handling a breach:

- Preparation — getting everything ready before anything even happens, like documenting procedures, setting up staffing plans, and training people so when an incident hits the team isn't scrambling
- Detection and analysis — using tools and defined processes to figure out if a breach actually occurred and how bad it is
- Containment — stopping the damage from spreading, this is high priority because you don't want the incident eating through more of the network or assets
- Eradication and recovery — fully removing all traces of the incident like malicious code and vulnerabilities, then restoring the affected systems back to a secure state, also called IT restoration
- Post-incident activity — writing up what happened, reporting to leadership, and figuring out lessons learned so the org handles it better next time
- Coordination — sharing information and reporting incidents throughout the whole process based on the organization's standards, this also keeps everything compliant with legal requirements

## Playbooks and SIEM Working Together

The way it works in practice is SIEM throws an alert and then the analyst grabs the right playbook and follows it. Like if there's a potential malware attack the playbook walks you through it — first you assess whether the alert is even valid by looking at the log data, then you contain the malware by isolating the infected system so it doesn't spread, then you eradicate all traces and restore the system using a clean backup from before the outbreak, and finally you do post-incident stuff like writing a final report for stakeholders or reporting to authorities like the FBI if it's serious enough.

## Playbooks and SOAR

SOAR stands for security orchestration automation and response and it's basically software that automates the repetitive tasks that SIEM and other tools generate. So instead of an analyst manually blocking an account after too many failed login attempts a SOAR just does it automatically, then the analyst comes in and uses the playbook to handle the rest. SOAR and playbooks together mean less manual work on the boring repeated stuff and more focus on the actual complex decisions that need a human.