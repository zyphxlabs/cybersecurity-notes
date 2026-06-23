# Course 1 Module 2

## How Attacks Started

Brain virus came in 1986 when Alvi brothers made it just to track pirated software copies, it spread through infected disks and jumped to every computer it touched, didnt destroy anything just slowed everything down globally within months but it was the first time organizations realized they actually need a security plan
Morris worm came in 1988 when someone built it just to measure how big the internet actually was but there was a bug in it that made it keep reinstalling itself on the same machines over and over until they crashed, ended up taking down 6000 computers which was 10% of the whole internet at that time and caused millions in damages, after this CERTs were created which basically are teams that exist specifically to respond to these kinds of threats

## Internet Age Attacks

LoveLetter hit in 2000 and it came through email with the subject "I Love You" and an attachment, people opened it because obviously who wouldnt and it just scanned their contacts and sent itself to everyone, infected 45 million computers and caused $10 billion in damages, this was basically the first time social engineering was used at that massive scale, showed that you dont need to be a technical genius you just need to know how people think
Equifax breach happened in 2017 when attackers got into a credit reporting agency, the thing is it wasnt even one vulnerability it was multiple known issues that nobody ever bothered to patch, they stole 143 million customer records including social security numbers, birth dates, addresses, credit card numbers, Equifax ended up paying $575 million to settle with the government, basically put every company on notice that ignoring vulnerabilities has a real financial cost

## Attack Types

**Phishing** is tricking people through communications, theres a bunch of types:

- BEC which is business email compromise, impersonates someone you know to get financial info
- Spear phishing which targets a specific person or group
- Whaling which is basically spear phishing but aimed at executives, people with high authority and privilege
- Vishing uses voice calls
- Smishing uses text messages

**Malware** is software built specifically to cause damage, different types do different things:

- Virus needs a user to actually open something, then it hides in files and spreads
- Worm spreads on its own, no user action needed at all
- Ransomware encrypts your data and holds it hostage until you pay
- Spyware just sits there silently collecting and selling your data without you knowing
- 
**Social engineering** is the technique where you trick someone into doing what you want and it works because of psychology honestly, humans are curious emotional creatures and if someone speaks to them nicely for long enough they start trusting them completely, attackers use things like authority, urgency, intimidation, familiarity, scarcity and consensus to get people to act without thinking
Some social engineering methods are interesting like:

- Social media phishing where they research about you first before attacking
- Watering hole attack where they target a site they know you visit regularly
- USB baiting which is literally just leaving a USB somewhere for someone to find and plug in
- Physical social engineering where someone pretends to be an employee or vendor to get physical access

## CISSP Eight Security Domains

Security and risk management is the foundation one, its about defining goals, managing risk, staying compliant with regulations like HIPAA and making sure the organization can keep running even if something bad happens
Asset security is about protecting both digital and physical assets, like when a company is throwing out old computers they need to properly wipe the drives not just trash them
Security architecture and engineering is making sure the right tools and systems are actually in place and configured properly, like setting up firewalls to block certain traffic
Communication and network security is about keeping the network itself secure, blocking employees from connecting to random public hotspots and setting up VPNs for people working remotely
Identity and access management is controlling who gets access to what, both physically like keycard access to rooms and digitally like user permissions on systems
Security assessment and testing is running audits and testing to make sure controls are actually working, like checking who has access to payroll information
Security operations is the reactive one, investigating incidents when they happen and following playbooks to respond, like when an unknown device connects to the network
Software development security is about baking security into the development process from the start, advising dev teams on things like password policies when theyre building apps

## Threat Actor Types

APT stands for advanced persistent threat and these are most interesting and scary ones, they are skilled attackers who research their targets first and then just sit inside the network quietly for months or even years without being detected, they usually go after infrastructure, government agencies or intellectual property
Insider threat is someone who already has authorized access to the systems and abuses it, could be motivated by money, sabotage or espionage and theyre hard to catch because theyre already inside and look like they belong there
Hacktivist is someone politically motivated who uses hacking to push an agenda or make a point, they usually go after governments or corporations
For hackers generally theres three categories:

- Authorized hackers also called ethical hackers, they follow the law and find vulnerabilities to help organizations fix them
- Semi-authorized are researchers who find vulnerabilities but dont exploit them
- Unauthorized are the malicious ones who break the law and sell stolen data for profit