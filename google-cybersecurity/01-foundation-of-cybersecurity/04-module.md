**Module 4 – Core Tools & Languages**

Logs are basically just records of everything happening inside an organization's systems, like who signed in, what was accessed, when it happened, that kind of stuff. security teams use them to spot anything weird going on, but the problem is there can be thousands of logs and manually going through all of them would take hours or even days which is just not realistic.

that's where SIEM tools come in, SIEM stands for Security Information and Event Management and what it does is it collects all that log data from multiple places and analyzes it automatically, so instead of reading through everything yourself it just throws alerts at you for the stuff that actually matters. two common ones are Splunk and Chronicle, Splunk is self-hosted meaning you run it on your own infrastructure, Chronicle is cloud-native so it's Google's version and being cloud-native means they can push new features faster. both do the same core thing though — collect, filter, analyze, alert.

playbooks are basically documented step-by-step procedures for when something happens. every organization has their own but the idea is the same, so when an incident hits you're not guessing what to do, you just follow the playbook. two important ones in forensics are:

- **chain of custody** – tracks who had the evidence, when, and where, basically every time evidence moves it gets documented so nobody can question its integrity
- **protecting and preserving evidence** – this one is about handling volatile digital evidence properly, volatile meaning data that just disappears if the device powers off, so you work from copies never the original

packet sniffers like Wireshark and tcpdump are tools that capture and analyze all the data traffic moving through a network, useful when you need to actually see what's flowing through the pipes.

Linux is an open-source operating system, meaning the code is public and anyone can contribute to it, unlike Windows or macOS. it doesn't have a regular GUI-style interface, you work through a command line which is just text-based commands, and as an entry-level analyst you'd mainly use it to look through logs and investigate things like unusually high network traffic.

SQL is a language specifically made for talking to databases, a database can have millions of data points so you use SQL to query it and pull only the specific information you actually need instead of drowning in everything.

Python is for automating repetitive tasks that would otherwise take forever manually and also where human error is more likely if done by hand, stuff that needs high accuracy and runs over and over is basically what Python is for.

other tools worth knowing:

- **IDS (Intrusion Detection System)** – monitors system activity and alerts on possible intrusions by scanning network packets
- **antivirus software** – scans memory and files to detect and remove malware
- **encryption** – converts readable data into ciphertext so unauthorized people can't read it, main goal is confidentiality
- **pen testing** – simulated attacks done on purpose to find vulnerabilities before real attackers do