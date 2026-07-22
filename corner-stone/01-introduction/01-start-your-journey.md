## Start Your Cyber Security Journey

Offensive security is basically when you think like an attacker, you're legally hacking into systems yourself to find the weak spots before some real bad actor gets there first and people who do this as a career are called penetration testers.

Defensive security is the other side, here you're the one protecting things, monitoring alerts, catching threats before they become actual incidents and responding when something does go wrong. SOC analysts are the ones sitting in this role every single day.

## Search Skills

### Google Dorking

Search engines are honestly so underused and most people just type something in and call it a day but there's actually a precise way to search that saves you hours:

- `"exact phrase"` — finds those exact words together
- `site:example.com` — only pulls results from that specific website
- `filetype:pdf` — gives you only that file type
- `-word` — cuts that word out of your results completely
- Example: `pyramids -tourists` gives everything about pyramids but removes all the tourist stuff

### Shodan

Shodan is basically a search engine but instead of websites it finds internet connected devices servers, cameras, routers, industrial systems, anything exposed online. During a penetration test its useful to just see what a target is actually running without even touching it directly. It has filters too:

- `country:PK` — narrows it to that country
- `port:22` — filters by open port
- `hostname:example.com` — filters by hostname

### VirusTotal

VirusTotal takes a suspicious file or URL and runs it through 70+ antivirus engines all at once and just shows you how many flagged it. Blue teamers use this constantly when investigating something sketchy, way faster than checking engines one by one yourself.

### CVE and CVSS

Every known vulnerability gets its own unique ID called a CVE, like CVE-2024-1337, and then it gets a CVSS score from 0 to 10 that basically tells you how serious it is, higher the score the more urgent the fix. ExploitDB actually has real exploit code for most of these CVEs which is useful for research.

### Man Pages

Every Linux command already has its own built in documentation so `man nc` opens the full manual for netcat and `man nmap` does the same for nmap. This should honestly be the first place you check before going to Google.

### GitHub for Security Research

Researchers put CVE proof of concepts and all kinds of tools on GitHub so searching a CVE number directly is a fast way to find analysis and sometimes working exploits. But not every PoC on there is reliable, some are broken and some are actually malicious on purpose so you always verify before running anything from a random repo.