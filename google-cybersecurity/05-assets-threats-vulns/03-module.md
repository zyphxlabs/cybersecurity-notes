## Vulnerabilities and exploits

Vulnerability is a weakness that can be exploited by a threat and the word can is important here because it doesnt mean it will always get exploited it just means its possible an exploit is basically the actual way of taking advantage of that weakness like a burglar using a rock to break a window is exploiting the vulnerability of glass being breakable

vulnerability management is the process security teams use to find and patch these things before they become a real problem its basically a four step cycle

- identify vulnerabilities
- think about how they could be exploited
- prepare defenses
- evaluate those defenses

once step four ends it just starts over again since new vulnerabilities keep showing up all the time this is why having diverse security teams help since more perspectives mean more ways to catch stuff

zero day is when an exploit happens that nobody knew about before basically zero days notice to fix it before its already being used against you these are the scariest kind since you cant plan defenses for something you didnt even know existed

## CI CD pipeline security

CI CD stands for continuous integration continuous delivery and continuous deployment its basically automating the whole software release process from writing code to pushing it live

- continuous integration is when developers merge code often and it automatically builds and tests itself so bugs get caught early
- continuous delivery means code is always ready to release but usually still needs manual approval before going to production
- continuous deployment is fully automated no manual approval needed changes go straight to production if they pass checks

security actually benefits from this automation since you can build checks right into the pipeline like DAST which tests running apps for vulnerabilities or compliance checks that make sure everything follows the rules

common vulnerabilities in CI CD pipelines

- insecure dependencies using third party libraries that have known CVEs
- misconfigured permissions weak access control on repos and tools
- lack of automated security testing meaning no SAST or DAST in place
- exposed secrets like hardcoding API keys or passwords directly in code
- unsecured build environments where the servers running the pipeline arent hardened

fixing all this basically comes down to devsecops mindset meaning security gets built in from the start not added later also using least privilege MFA RBAC updating dependencies regularly and using proper secret management tools like hashicorp vault instead of just typing secrets into code

## CVE list and vulnerability databases

Exposure is different from vulnerability an exposure is a mistake that can be exploited while vulnerability is the actual weakness like leaving a document near an open window is an exposure since it could get blown away

CVE list stands for common vulnerabilities and exposures list its basically an open dictionary of known vulnerabilities and exposures it was created by MITRE back in 1999 MITRE is a nonprofit rnd group funded by the US government

anyone can report a CVE but it has to pass through a CNA which stands for CVE numbering authority before it gets an official ID there are four criteria a vulnerability must meet to get listed

- must be fixable independently of other issues
- must be recognized as a real security risk
- must come with supporting evidence
- must only affect one codebase

after getting listed a lot of these CVEs get reviewed further by databases like NIST national vulnerabilities database which uses CVSS common vulnerability scoring system to score how severe something is on a scale of 0 to 10 anything below 4 is low risk anything above 9 is critical and needs fixing immediately

## OWASP top 10

OWASP stands for open worldwide application security project its a nonprofit that shares info tools and events focused on web security their most useful resource is the OWASP top 10 which is a list theyve published since 2003 showing the most commonly targeted vulnerabilities in new or custom built software

the vulnerabilities that usually show up on this list

- broken access control when restrictions on what users can do fail
- cryptographic failures like using weak hashing such as MD5 instead of proper encryption
- injection when malicious code gets inserted into an app usually through things like login forms
- insecure design missing or poorly built security controls from the start
- security misconfiguration like leaving default settings on when deploying servers
- vulnerable and outdated components using old unmaintained open source libraries
- identification and authentication failures apps failing to properly verify who should have access
- software and data integrity failures poorly reviewed updates that can lead to supply chain attacks like the solarwinds attack in 2020
- security logging and monitoring failures not keeping proper records of events like login attempts
- server side request forgery SSRF when attacker manipulates a server into fetching unauthorized data

## OSINT and gathering intelligence

OSINT stands for open source intelligence its basically collecting and analyzing info from public sources to create usable intelligence information is just raw data or facts while intelligence is the analysis of that info to actually make decisions

security teams use OSINT to identify threats and vulnerabilities like monitoring hacker forums for discussions about new exploits some common OSINT tools

- virustotal for scanning suspicious files domains urls and ips
- mitre attck a knowledge base of real world adversary tactics
- osint framework a directory of osint tools for different platforms
- have i been pwned for checking breached email accounts

## Vulnerability scanning

Vulnerability scanner is software that compares known vulnerabilities and exposures against whats actually on your network it scans five attack surfaces which are perimeter network endpoint application and data layers

there are a few types of scans based on approach

- external scans test outward facing systems like websites and firewalls
- internal scans test stuff inside the network like application software
- authenticated scans log in as a real user to check for stuff like broken access control
- unauthenticated scans simulate someone with no access at all trying to get in
- limited scans check specific devices like just a firewall
- comprehensive scans check everything connected to the network

discovery scanning should happen before limited or comprehensive scans just to get a general idea of whats even on the network

## Patching and updates

Patch update is basically fixing known vulnerabilities in software sometimes patches come out because of a zero day being discovered

there are two ways updates get installed

- manual updates where IT or user installs it themselves gives more control but stuff can get forgotten
- automatic updates where system installs it on its own CISA actually recommends this option but if vendor didnt test well it can cause instability

end of life software or EOL is software that no longer gets updates because the company moved on to newer versions CISA recommends ditching EOL software since its basically an unfixable risk but businesses dont always follow that since replacing old tech is expensive

wannacry attack in 2017 is a good example of what happens when patches get ignored it hit computers in over 150 countries and caused about 4 billion dollars in damage even though the patch for that vulnerability was already available months before

## Penetration testing

Penetration test or pen test is a simulated attack used to find vulnerabilities its basically ethical hacking since its authorized unlike vulnerability assessment which just finds weaknesses pen test actually exploits them to see what could really happen

organizations regulated by PCI DSS HIPAA or GDPR are required to do pen testing regularly for compliance

types of pen test teams

- red team simulates the attack
- blue team focuses on defense and response
- purple team is a mix of both working together

pen testing strategies based on how much access tester has

- open box tester has full internal knowledge also called white box
- closed box tester has no internal access basically like a real hacker also called black box
- partial knowledge tester has limited access also called gray box

closed box tends to give the most realistic results since it mimics an actual attacker

bug bounty programs are when companies pay freelance hackers to find and report vulnerabilities hackerone is a popular place where ethical hackers find these bounties

## Attack surface and hardening

Attack surface is all the potential vulnerabilities a threat actor could exploit organizations have both a physical and digital attack surface physical includes people and devices like an unattended laptop in a coffee shop digital includes anything beyond the firewall that connects online

cloud computing basically expanded the digital attack surface a ton since now people can access company info from anywhere in the world without even touching the internal network

security hardening is the process of strengthening a system to reduce its vulnerabilities and attack surface basically minimizing entry points so theres less to protect things like policies and access controls are common ways to harden the physical attack surface

## Threat actors and hackers

Threat actor is any person or group that presents a security risk this can be intentional or accidental threat actors are usually grouped into five categories

- competitors rival companies who benefit from leaked info
- state actors government intelligence agencies
- criminal syndicates organized groups doing it for money
- insider threats people with authorized access who misuse it
- shadow IT employees using unapproved tech like personal email for work stuff

hacker is anyone who uses computers to gain unauthorized access there are three types based on intent

- unauthorized hackers also called malicious hackers some are called script kiddies if they just use pre written code from others
- authorized or ethical hackers who work to improve security
- semi authorized hackers like hacktivists who break rules but arent exactly malicious usually trying to expose stuff for a cause

advanced persistent threat or APT is when a threat actor stays hidden inside a system for a long time usually associated with state sponsored actors theyre patient and often target private companies first as a stepping stone toward bigger targets like government systems

attackers usually get in through common attack vectors

- direct physical access
- removable media like USB drives
- social media
- email
- wireless networks
- cloud services
- supply chain through third party vendors

## Attacker mindset and attack vectors

Attack vector is the pathway attackers use to get through defenses same as doors and windows of a home being exploitable features employees sometimes exploit these vectors accidentally too like oversharing on social media without meaning to cause harm

practicing an attacker mindset basically means asking how would i exploit this and it follows a process

- identify a target
- figure out how it can be accessed
- evaluate which vectors can be exploited
- find tools and methods to actually do it

defending against these attack vectors usually comes down to educating users applying least privilege using proper security tools like antivirus and building a diverse security team since different perspectives catch different things

simulations are also used to test defenses proactively or reactively proactive is basically red team stuff where you act like the attacker reactive is blue team stuff where you gather info and respond like using vulnerability scans then going through identification vulnerability analysis risk assessment and remediation steps

## Brute force attacks

Brute force attack is basically trial and error to guess login credentials there are a few variations

- simple brute force just guessing random combinations
- dictionary attack using a list of commonly used passwords
- reverse brute force starting with one password and trying it across many accounts
- credential stuffing using stolen credentials from other breaches to get into new accounts pass the hash is a specific version of this using stolen hashed credentials

attackers use tools to automate this instead of doing it manually like aircrack-ng hashcat john the ripper ophcrack and thc hydra

ways to prevent brute force attacks

- hashing and salting to make passwords harder to reverse
- MFA to add extra verification steps
- captcha to prove the user is human
- password policies requiring length and complexity plus lockout after failed attempts

## Defense in depth

Defense in depth is basically a layered approach to security also called the castle approach since its like how medieval castles had multiple layers of defense like moat walls and watch towers each layer covering for the weakness of the other

in cybersecurity this model uses five layers

- perimeter layer mainly authentication stuff like usernames and passwords
- network layer more about authorization includes things like firewalls
- endpoint layer protecting actual devices like laptops and servers using antivirus
- application layer security built into the app itself like MFA
- data layer protecting the actual sensitive data using stuff like asset classification

info passes through all these layers whenever its exchanged over a network and if one layer fails theres still another layer standing in the way

## Vulnerability assessment process

Vulnerability assessment is the internal review process a company does on its own security systems similar to how CVE list works but done in house it follows a four step process

- identification using scanning tools and manual testing to find vulnerabilities basically taking a snapshot of current state
- vulnerability analysis digging into each vulnerability to find the actual root cause
- risk assessment scoring each vulnerability based on severity and likelihood of being exploited
- remediation actually fixing the vulnerabilities based on their score usually a joint effort between security and IT teams

this whole process is basically how organizations figure out where to focus their limited resources since there are always more vulnerabilities than people to fix them