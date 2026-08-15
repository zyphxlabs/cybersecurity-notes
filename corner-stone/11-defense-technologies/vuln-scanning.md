## Vulnerability Scanning Basics
Think of it like a small house where the roof has tiny holes, if you dont fix them water gets in during rain and damages furniture, dust and insects sneak in too. Those small holes are basically weaknesses and if left untreated they cause bigger problems later, in security we call these weaknesses vulnerabilities. Fixing that roof is basically patching, the same concept applies to digital devices, software and hardware both carry vulnerabilities that attackers look for and exploit to get into a system. The tricky part is you cant just see these vulnerabilities like you see a hole in a roof, you have to actually go hunt for them, and once found you patch them to close the gap

Vulnerability scanning is basically inspecting systems to find these weaknesses. Since organizations hold a lot of critical data they need to scan regularly, attackers can exploit unpatched vulnerabilities and cause serious loss. Its also often a compliance requirement, some standards want scans done quarterly others want it once a year. Doing this manually is slow and easy to miss stuff especially on bigger networks so thats where automated vulnerability scanners come in, you just give it an ip or a network range and it checks everything and gives you a readable report. After vulnerabilities are found the fixes applied to the software or system are called patches

## Types of Scans
Authenticated vs unauthenticated is one major way to split scan types

- Authenticated scans — need credentials of the host, gives deeper visibility into configs and installed apps, shows what an attacker could exploit if they already have access, example would be scanning an internal database with its credentials
- Unauthenticated scans — no credentials needed just the ip, shows what an external attacker without access could exploit, less resource intensive and easier to set up, example would be scanning a public facing website

Internal vs external is another way to split them

- Internal scans — done from inside the network, focuses on what could be exploited once an attacker is already inside
- External scans — done from outside the network, focuses on what could be exploited from outside before even getting in

Usually authenticated scans get used more for internal scanning and unauthenticated ones get used more for external scanning

## Vulnerability Scanning Tools
There are a bunch of tools out there for automated scanning each with their own strengths

Nessus started as an open source project back in 1998 and got acquired by Tenable in 2005 turning it into proprietary software. It has a free version with limited features and a paid version with advanced scanning unlimited scans and support, needs to be deployed and managed on premises

Qualys came out in 1999 as a subscription based solution, it does continuous scanning plus compliance checks and asset management and alerts automatically when it finds something. Its cloud based so theres no extra hardware cost or effort needed to maintain it

Nexpose was made by rapid7 in 2005, it continuously finds new assets on the network and scans them, gives risk scores based on asset value and how impactful the vulnerability is, also does compliance checks. It can be deployed on premises or hybrid

Openvas is open source made by greenbone security, its more basic compared to the commercial tools but still gives a full vulnerability scanning experience using its own vulnerability database, good fit for smaller orgs or individual systems

Almost every scanner gives you reporting after a scan, listing the vulnerabilities found their risk scores and descriptions, some even give remediation steps and let you export reports in different formats. Choosing the right tool comes down to scope resources depth of analysis and other factors like that

## CVE and CVSS
Imagine working help desk for it support handling hundreds of complaints daily, you'd want a unique number for each complaint so you can track it later, thats basically what cve does for vulnerabilities. Cve stands for common vulnerabilities and exposures, its a unique id given to a newly discovered vulnerability, developed by mitre corporation and published in a public cve database so people can find details and apply fixes. A cve number has three parts

- CVE prefix — always starts with cve
- Year — the year it was discovered like 2024
- Arbitrary digits — four or more digits at the end like 9374

Cvss stands for common vulnerability scoring system, going back to the help desk analogy you'd want to prioritize complaints by severity, cvss does that for vulnerabilities by giving them a score from 0 to 10 based on factors like impact and how easy it is to exploit

- 0.0-3.9 — low
- 4.0-6.9 — medium
- 7.0-8.9 — high
- 9.0-10 — critical