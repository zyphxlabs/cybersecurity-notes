## CISSP Eight Security Domains

Security posture is basically how well an organization can defend its important things and respond when things go wrong. CISSP created 8 domains to help security teams organize their work and find gaps before those gaps turn into real problems.

## Domain 1 – Security and Risk Management

This one covers the big picture stuff like setting security goals, keeping compliance in check, handling legal rules and making sure the business can keep running even when something bad happens. The basic idea is if you have clear goals and the right rules in place you can reduce how badly a risk affects you. Ethics also comes here, basically don’t be careless or commit fraud.

## Domain 2 – Asset Security

This is about protecting both physical and digital assets through their whole life, storage, upkeep, keeping them, and even destroying them. Like if a hard drive needs to be thrown away you can’t just toss it, it has to be properly destroyed so attackers can’t recover data from it. You need to know what assets you have and who can access them, otherwise your security posture means nothing.

## Domain 3 – Security Architecture and Engineering

Focused on making sure the right tools, systems and processes are actually in place to protect data. The big idea here is shared responsibility which means everyone in the organization has a role in keeping things secure, not just the security team. If employees are encouraged to report issues, a lot of problems get caught early.

## Domain 4 – Communication and Network Security

This one is about keeping networks and wireless communications safe whether people are on-site, remote or using the cloud. Remote workers are a big focus here because if someone connects over public Wi-Fi or an unsafe Bluetooth connection they can expose the whole organization. Security teams can also remove access to those channels at the organization level so people don’t accidentally do something risky.

## Domain 5 – Identity and Access Management (IAM)

IAM is about making sure only the right people can access the right things. There are 4 parts to it:

- Identification – user proves who they are using username, access card or biometrics  
- Authentication – checking step like a password or PIN  
- Authorization – what they are actually allowed to do based on their role  
- Accountability – tracking and logging what users do  

If everyone is using the same admin login you can’t track who did what and in a breach you would have no idea who was the attacker and who was a real user.

## Domain 6 – Security Assessment and Testing

This domain is about finding out if your security controls are actually working. Teams run control tests, collect data, do audits and bring in penetration testers to find weaknesses before attackers do. Like if an audit shows a weakness they might add something like MFA as a new control. The whole point is constantly checking that what you have in place is actually working.

## Domain 7 – Security Operations

Once an incident happens this domain kicks in. The team investigates quickly to stop it from getting worse and once the threat is controlled they collect digital and physical evidence for a forensic investigation to figure out when, how and why it happened. The goal is to learn from it and stop the same thing from happening again.

## Domain 8 – Software Development Security

Security must be built into every stage of the software development life cycle, not added at the end. So during design there is a secure design review, during development and testing there are code reviews, and during deployment there is penetration testing. If you skip any of these steps you are basically releasing vulnerable software into production.

---

## Threats, Risks and Vulnerabilities

These three are related but not the same. A threat is anything that could harm assets, a risk is the chance of that threat actually happening, and a vulnerability is the weakness the threat uses. Both a vulnerability and a threat must exist together for there to be real risk.

Organizations rate risks in three levels:

- Low – public info, would not hurt reputation or money if exposed  
- Medium – non-public info, some financial or reputation damage possible like leaking earnings early  
- High – protected by law like PII, SPII or IP, serious consequences if leaked  

Social engineering is one of the main threats and it works by using human psychology basically tricking people into giving up information or access. Phishing is the most common type where you get an email that looks real but is fake.

## Ransomware

Ransomware is when attackers lock your data by encrypting it and demand money before giving you the decryption key. Once used it can stop network systems, lock devices and make everything unusable. Ransom talks often happen on the dark web because it gives attackers anonymity.

## The Three Layers of the Web

- Surface web – what most people use, accessible through normal browsers  
- Deep web – needs login or permission, like a company intranet  
- Dark web – needs special software to access, used by criminals because it is hidden  

## Impacts of Threats, Risks and Vulnerabilities

Financial impact is the most obvious one, stopped services, cost to fix the issue and possible legal fines can all add up fast. Then there is identity theft where stolen PII or SPII gets sold on the dark web and the organization has no control over what happens after that. And finally reputation damage which can last a long time, customers may not return after their data is leaked and legal penalties often follow too.

---

## NIST Risk Management Framework (RMF)

NIST created a 7 step framework for managing security and privacy risks. The steps are:

- Prepare – get everything ready before a breach happens, identify risks and controls  
- Categorize – figure out how risk affects confidentiality, integrity and availability of systems  
- Select – choose the right controls and document them, like updating playbooks  
- Implement – actually put the security and privacy plans into action  
- Assess – check if the controls you set up are working correctly  
- Authorize – take responsibility for the risks that exist and create reports, action plans and goals  
- Monitor – keep watching systems daily to make sure everything still matches security goals  

---

## Notable Vulnerabilities

- ProxyLogon – affects Microsoft Exchange, lets attackers skip login and run harmful code remotely  
- ZeroLogon – targets Microsoft’s Netlogon system, breaks the identity check process  
- Log4Shell – lets attackers run Java code remotely or steal sensitive information from internet-connected systems  
- PetitPotam – affects Windows NTLM, lets a local network attacker trigger an authentication request they should not be able to  
- Security logging and monitoring failures – when logging is weak so attackers can exploit systems without anyone noticing  
- Server-side request forgery – tricks a server into accessing internal resources it should not, can be used to steal data  

The key with all of these is that fixes exist but if you don’t apply them they are useless. Vulnerability management is a constant job of watching, finding and fixing issues before attackers find them first.