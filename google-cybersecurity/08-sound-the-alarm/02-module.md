## Incident escalation

Incident escalation is the process of identifying a potential security incident triaging it and if needed handing it off to someone more experienced. Not every incident needs to be escalated so part of the job is figuring out which ones do. As entry level analyst you probably wont be handling incidents alone but you still need to know how to evaluate and pass it to the right person.

Two skills matter most here attention to detail and knowing your organization escalation guidelines. Attention to detail helps you catch when something feels off in the network or system while knowing the guidelines helps you actually escalate it the right way. Bigger orgs have many levels of security team from CISO down to engineering PR and even legal each playing their part depending on the incident.

If a small issue sits unescalated too long it can turn into something that costs the company money exposes customer data or damages reputation so basically first step in the assembly line matters a lot for everything after it.

## Breach notification laws

Lots of countries have breach notification laws which require companies to notify people if their PII got exposed in a breach. PII here includes stuff like ssn drivers license numbers medical records addresses etc. These laws get updated regularly so staying aware of them is part of the job.

## Low level security issues

- One failed login attempt on an account
- Employee downloading unapproved software on work laptop

These arent huge threats on their own but still need investigating because a few failed logins could turn into 15 attempts in 30 mins which might mean an actual attacker is trying to get in. Same with unapproved downloads it could have malware hidden in it.

## Escalation process

Every company has different protocol for this called an escalation policy. It defines who gets notified when an alert comes in and who to contact if first responder isnt available. It also tells you how to escalate like through IT desk or an incident management tool or just direct messaging the team.

## Incident classification types

Malware infection happens when malicious software designed to disrupt systems gets into the org network. Can be simple like phishing or complex like ransomware where attacker locks your data until you pay them. This one is especially damaging because of how much sensitive data usually sits in these systems.

Unauthorized access happens when someone gets into a system or app without permission often through brute force attacks trying different password combos. All of these need escalating but urgency depends on how critical the system is.

Improper usage happens when an employee violates the acceptable use policy. Sometimes its unintentional like using company system to access a friends data without realizing it broke policy and sometimes its intentional. Since its hard to tell which one it is these should always go to a supervisor.

## Roles in the escalation process

- Data owner - decides who can access edit use or destroy the data accountable for its classification and protection unauthorized access issues go to them
- Data controller - decides how and why data gets processed makes sure its used and stored following privacy regulations sensitive customer data risks go here
- Data processor - usually a vendor that processes data on behalf of controller processing issues get escalated to whoever manages that third party
- Data custodian - grants and revokes access creates storage policies and monitors data gets notified when controls need strengthening or get compromised
- Data protection officer DPO - monitors internal compliance with data protection procedures and advises the team gets notified when standards are violated

As entry level you'll mostly escalate to your direct supervisor but knowing these roles helps you understand who ultimately needs to know.

## Incident criticality and urgency

A small unescalated issue like weird log activity in a banned app can snowball into a full data breach affecting manufacturing or other operations if nobody flags it in time. Incidents can start at medium criticality if analyst doesnt have full info yet then get bumped up or down once a more experienced handler reviews it.

Urgency really depends on what asset is affected. Forgotten password with a few failed logins is low urgency but unauthorized access to something like a manufacturing app or a PII database is high urgency because the damage potential is way bigger.

## Escalation policy and analyst mindset

Escalation policy is basically the set of actions defining who gets notified and how the incident should be handled. It wont always go smoothly like what if your supervisor is out of office that day the incident still needs to go somewhere. Its good to bookmark the policy on your work device instead of trying to memorize it.

Confidence matters here trust your instincts but also dont be afraid to ask questions when unsure asking shows you're serious about doing the job right. Not all incidents are equal so knowing which assets matter most to your org through onboarding docs supervisor conversations or security policies helps you prioritize correctly. Incidents affecting core business operations always take priority over ones that dont like unauthorized access to a manufacturing app being more urgent than malware on some legacy system nobody uses anymore.

## Juliana Soto case study part 2

Juliana is monitoring logs and gets an alert about an employee account locked after 10 failed logins which per policy needs to go to the password protection team. Right after that another alert comes in about an unknown source trying to compromise the system storing customer bank info. She realizes this second one is way more urgent since it involves sensitive financial data affecting hundreds of customers so she handles that one first following the escalation policy step by step then goes back and escalates the lower priority login issue. Her supervisor is impressed with how she prioritized and followed the process correctly showing that attention to detail plus knowing whats actually important to the org makes a huge difference in escalation.