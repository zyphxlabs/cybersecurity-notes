## Social engineering basics

Social engineering is a manipulation technique that exploits human error to gain private info access or valuables its basically tricking people instead of hacking systems directly it works due to psychology i guess humans are curious emotional creatures if someone speaks to them nicely for some time they end up trusting them

these attacks go through stages first attackers prepare by gathering info about the target then they build trust which is called pretexting basically pretending to be someone trustworthy after that they use persuasion to actually get the target to share info and finally they disconnect and disappear to cover their tracks

managerial controls like policies standards and procedures help defend against this like the patch management standard from NIST SP 800-40 but honestly the best defense is just teaching people what to look out for since attackers rely on us not thinking too much before acting

## Social engineering tactics

Twitter hack of 2020 is a good example of how dangerous this can be hackers called twitter employees pretending to be from IT department and used that basic trick to get access to internal tools letting them hijack accounts of politicians celebrities and entrepreneurs

common tactics to watch for

- baiting tempting someone into compromising security like leaving an infected USB drive somewhere
- phishing tricking people through digital communication mostly email
- quid pro quo promising a reward in exchange for info like fake loan officers offering lower interest rates
- tailgating following an authorized person into a restricted area also called piggybacking
- watering hole compromising a website that a specific group frequently visits like the holy water attack of 2020 that hit religious and charity sites

defense mostly comes down to staying alert on suspicious emails being careful about oversharing on social media and controlling curiosity when something feels too good to be true firewalls MFA blocklists and email filtering help layer the defense even more

## Phishing types

Phishing started way back in the 90s targeting aol instant messenger users through fake emails asking them to verify accounts this was one of the earliest cases of mass phishing which just means sending the same scam to a ton of people hoping someone falls for it

phishing evolved a lot since then and now includes multiple types

- email phishing sent through email pretending to be a trusted source
- smishing done through text messages including imessage or whatsapp
- vishing done through voice calls or messages
- spear phishing targeting specific people like accountants
- whaling targeting high ranking executives specifically

angler phishing came up later in the 2010s where attackers pretend to be customer service reps on social media targeting people who already complained publicly about a company its basically exploiting people who are already annoyed and looking for help

phishing kits are basically toolkits attackers use containing malicious attachments fake data collection forms and fraudulent web links designed to steal info or credentials

## Malware types

Malware is software designed to harm devices or networks it spreads in a bunch of ways like infected usb drives or just over the internet common types include

- virus malicious code that needs the user to activate it before it spreads by cloning itself into other files
- worm similar to virus but spreads on its own across a network without needing user action
- trojan malware disguised as a legit file or program named after the greek legend where soldiers hid inside a wooden horse to sneak into troy
- ransomware encrypts data and demands payment to restore access it makes itself known on purpose since otherwise it cant collect the ransom
- spyware collects and sells info without consent

adware is technically legit software used to show ads but a malicious version called PUA potentially unwanted application can get bundled with other programs without proper consent and mess with ads or slow down device scareware is another kind of PUA that tricks users with fake warnings to scare them into infecting their own device

fileless malware doesnt need to be installed since it hides in memory using programs already on the device making it harder to detect through normal methods

rootkit gives remote admin access to attackers usually spread using a dropper which is disguised as a normal file or a loader which downloads more malicious code afterward multi staged attacks often use loaders to set up things like botnets

botnet is a network of infected computers controlled by one attacker called the bot herder viruses worms and trojans are often used to initially infect devices and turn them into bots

cryptojacking is a newer type of malware that installs software to illegally mine cryptocurrency started around 2017 crypto mining is basically using computers to solve encrypted code to earn coins more computers mining means more coins found criminals realized they could just hijack other peoples computers to do this for free

signs of cryptojacking include slowdown high cpu usage random crashes fast draining battery and unusually high electricity bills IDS intrusion detection system helps catch abnormal activity like this but new malware can still slip past undetected defense includes using ad blockers browser extensions blocking malware disabling javascript and just staying updated on trends

## Web based exploits

Web based exploits are malicious code or behavior used to take advantage of coding flaws in web apps injection attack is when malicious code gets inserted into a vulnerable application and runs quietly in the background without the user knowing

cross site scripting or XSS is a type of injection attack that inserts code into a website through html and javascript giving attackers access to stuff like session cookies geolocation even webcams and mics there are three types

- reflected XSS script sent to server and reflected back during response usually through a malicious link
- stored XSS script injected directly on the server so it activates just by visiting the site
- DOM based XSS script exists in the actual webpage code itself and doesnt need server interaction to activate

## SQL injection

SQL is a programming language used to interact with databases SQL injection is an attack that executes unexpected queries on a database happens because of unsanitized input in places like login forms or search bars

three categories of SQL injection

- in-band the most common type where attack and result happen in the same channel like a vulnerable search box returning sensitive data directly
- out-of-band attacker uses a separate channel to launch and collect results from the attack very rare since it needs specific server features enabled
- inferential attacker cant see results directly but figures things out based on how the system responds like error messages

prevention mainly comes down to escaping user input properly using things like

- prepared statements executing SQL before passing to database
- input sanitization removing anything that could be interpreted as code
- input validation making sure input matches what the system expects

## Threat modeling

Threat modeling is the process of identifying assets their vulnerabilities and how theyre exposed to threats its usually tied closely to application security since apps handle huge amounts of data example given was the log4shell vulnerability CVE-2021-44228 which if unpatched allows remote code execution and can affect millions of devices

threat modeling generally follows six steps

- define the scope
- identify threats
- characterize the environment
- analyze threats
- mitigate risks
- evaluate findings

common frameworks used

- STRIDE made by microsoft focuses on six vectors spoofing tampering repudiation information disclosure denial of service and elevation of privilege
- PASTA process for attack simulation and threat analysis a risk centric model made by owasp leaders and versprite
- Trike open source and security centric focusing on permissions and privilege models
- VAST visual agile and simple threat modeling part of an automated platform called threatmodeler

## PASTA framework in detail

PASTA has seven stages using the example of a fitness app launching and needing to protect customer data

- stage one define business and security objectives basically figuring out what needs protecting and why
- stage two define technical scope identifying what parts of the app need evaluation this is basically the attack surface
- stage three decompose the application working with developers to build a data flow diagram showing how data moves and what protects it
- stage four perform threat analysis researching current attack trends relevant to the app
- stage five perform vulnerability analysis digging deeper into the root of potential vulnerabilities
- stage six conduct attack modeling testing vulnerabilities by simulating attacks using an attack tree which is basically a flow chart showing how an attacker could exploit something like SQL injection through unsanitized inputs
- stage seven analyze risk and impact combining everything gathered to give risk based recommendations to stakeholders

threat actors in general are categorized as internal like an employee intentionally causing harm or external like a hacker or competing business and the whole modeling process is basically about asking the right questions like what could go wrong and have we covered everything