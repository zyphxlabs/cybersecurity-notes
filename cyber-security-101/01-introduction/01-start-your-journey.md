# Start Your Cyber Security Journey

Offensive security is basically thinking like the attacker, you're legally breaking into systems yourself to find the weak spots before some actual bad actor does and the people who do this as a job are called penetration testers.

Defensive security is the opposite side, you're the one protecting, monitoring alerts, catching threats and responding when something goes wrong and SOC analysts are the ones doing exactly this every single day.

## Search Skills

### Google Dorking

Search engines are honestly the most underused tool and knowing how to use them properly saves you hours, most people just type stuff in the bar but there's actually a whole way to be precise about what you're looking for:

- `"exact phrase"` — finds those exact words together
- `site:example.com` — only searches within that specific website
- `filetype:pdf` — pulls up only that file type
- `-word` — removes that word from results
- example: `pyramids -tourists` gives you everything about pyramids but cuts out tourist stuff

### Shodan

Shodan is basically a search engine but instead of websites it finds internet connected devices, so servers, cameras, routers, industrial systems, anything exposed online. during a penetration test its really useful to just see what a target is actually running without even touching it. it has filters too:

- `country:PK` — narrows results to that country
- `port:22` — filters by open port
- `hostname:example.com` — filters by hostname

### VirusTotal

VirusTotal takes a suspicious file or URL and runs it against 70+ antivirus engines all at once and just tells you how many flagged it. blue teamers use this constantly when investigating something sketchy, way faster than checking engines one by one.

### CVE and CVSS

Every known vulnerability gets its own unique ID called a CVE, like CVE-2024-1337, and then it gets a CVSS score from 0 to 10 that basically tells you how dangerous it is, higher the score the more urgent it is to fix. ExploitDB actually has the real exploit code for most of these CVEs which is useful for research.

### Man Pages

Every Linux command has its own built in documentation already, so `man nc` opens the full manual for netcat and `man nmap` does the same for nmap. this should honestly be the first place you check before going to Google.

### GitHub for Security Research

Researchers put CVE proof of concepts and all kinds of tools up on GitHub so searching a CVE number directly is a fast way to find analysis and sometimes working exploits. but not every PoC on there is reliable, some are broken and some are actually malicious on purpose so you always verify before running anything you find from a random repo.