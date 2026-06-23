## Frameworks and Controls

Security frameworks are basically guidelines like a blueprint an organization follows to build out their security plans so they are not starting from scratch every time a threat shows up. They help with compliance too, like HIPAA in healthcare which forces medical people to keep patient data safe, and without a framework it would be super hard to know where to even begin with that.

Controls are  actually used to  reduce specific risks so the framework tells you what to do and the control is the thing you put in place to actually do it. Like if you have a HIPAA framework you might add MFA as a control so that patients have to verify themselves before accessing their own medical records.

Two frameworks worth knowing besides NIST are the Cyber Threat Framework (CTF) which was made by the U.S. government so that everyone in cybersecurity can use the same language when talking about threat activity makes sharing info way faster. And ISO/IEC 27001 which is an international one that any organization of any size can use to manage security of their assets like financial data, employee data, intellectual property and so on.

Controls break down into three types:

- Physical — gates, locks, CCTV, access badges, security guards
- Technical — firewalls, MFA, antivirus
- Administrative — separation of duties, authorization, asset classification

## Encryption, Authentication, Authorization

Encryption is when you take readable data and convert it into ciphertext which is basically scrambled nonsense that nobody can read until it gets decrypted back to its original form, this is how sensitive stuff like social security numbers stay protected even if someone gets their hands on the data.

Authentication is the part where you prove you are who you say you are, simplest version is a username and password but MFA takes it further by asking for something extra like a code sent to your phone or a biometric like a fingerprint or face scan. Biometrics are just unique physical things about you that can verify your identity like an eye scan or palm scan. There is an attack called vishing which exploits voice communication to impersonate someone and steal their identity which is wild because it basically weaponizes the authentication process itself.

Authorization is different from authentication, authentication is proving who you are, authorization is about what you are actually allowed to access after that. So a federal employee might authenticate normally but then get access to deep web or internal government data that a regular person would never see.

## CIA Triad

The CIA triad is the core model security people use to think about risk when setting up systems and policies, it stands for confidentiality, integrity, and availability and you will use this constantly as an analyst.

Confidentiality means only the people who are supposed to see something can see it, sensitive data on a need to know basis. This is backed up by least privilege which means users only get access to what they actually need for their job, nothing extra.

Integrity means the data is correct and trustworthy and hasn't been messed with, cryptography and encryption are used here to make sure unauthorized people can't tamper with it. Banks use this a lot, like if your spending pattern suddenly changes dramatically they will freeze the account because that might mean the data about who is spending is no longer reliable.

Availability means authorized people can actually get to the data when they need it, inaccessible data is useless and just breaks workflows. Banks also do this really well, they put a lot of effort into making sure account info is easily accessible on the web while still protecting it.

## NIST CSF Five Core Functions

NIST CSF is a voluntary framework that gives organizations standards, guidelines and best practices to manage cybersecurity risk, it has five core functions that cover basically the full lifecycle of handling a security incident.

- Identify — managing cybersecurity risk and understanding its effect on people and assets, like monitoring internal network devices to spot potential issues
- Protect — implementing policies, procedures, training and tools to mitigate threats, studying historical data and improving policies falls here
- Detect — identifying potential incidents and improving monitoring speed and efficiency, like configuring a new security tool to flag low/medium/high risk and alert the team
- Respond — containing, neutralizing, and analyzing incidents then improving the process, like documenting an incident and suggesting fixes so it doesn't happen again
- Recover — returning affected systems to normal operation, restoring things like financial or legal files that got hit in a breach

## OWASP Security Principles

OWASP is a nonprofit focused on improving software security and they put out a bunch of principles that are actually useful in day to day analyst work not just in theory.

Minimize attack surface area means you reduce all the places a threat actor could exploit, things like disabling unused software features, restricting access, making passwords harder. Least privilege means users get the bare minimum access they need, so if your credentials get compromised the attacker only gets a tiny slice of what exists. Defense in depth is layering multiple controls so a threat actor has to break through several things instead of just one, MFA plus firewall plus IDS plus permission settings all stacked up.

Separation of duties prevents any one person from having so much power they could just do something fraudulent undetected, like the person who prepares paychecks shouldn't also be the one signing them. Keep security simple because overly complicated controls become unmanageable and make collaboration harder. Fix security issues correctly means when something goes wrong you find the actual root cause and fix it properly then test to make sure it actually worked, not just patch the symptom.

Four more OWASP principles worth knowing:

- Establish secure defaults — an app should be secure out of the box, making it insecure should require extra effort not the other way around
- Fail securely — if a control fails it should default to the most secure option, like a firewall failing should close all connections not open them
- Don't trust services — third party partners have different security policies so you verify their data yourself before trusting it, like an airline double checking reward points from a vendor before showing customers their balance
- Avoid security by obscurity — you can't rely on hiding source code or keeping details secret as your main security strategy, real security comes from password policies, defense in depth, network architecture and audit controls

## Security Audits

A security audit is basically a formal review of an organization's controls, policies and procedures measured against what they are supposed to be doing. Internal audits are usually done by a compliance officer, security manager and the security team, and entry level analysts can be asked to help with parts of it. The whole point is to find gaps, avoid fines from government agencies, and improve the organization's security posture.

Internal audits have five elements:

- Establish scope and goals — scope is what people, assets, policies, procedures and technologies are being assessed, goals are what the org wants to achieve
- Risk assessment — identifying potential threats, risks and vulnerabilities to figure out what controls need to be in place
- Controls assessment — reviewing existing assets and categorizing controls as administrative, technical or physical to see if they are actually working
- Assess compliance — checking if the org is following the regulations they are legally required to follow, like GDPR and PCI DSS if they operate in the EU and take card payments
- Communicate results — summarizing everything for stakeholders, existing risks, how urgent they are, compliance gaps, and recommendations for improving security posture

A real example of an audit catching something useful is a team doing an internal password audit, finding out a ton of passwords were weak, and then the compliance team stepping in to enforce stricter password policies after that.