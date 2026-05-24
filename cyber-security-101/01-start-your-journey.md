# Start Your Cyber Security Journey

## Offensive Security
Offensive security is about thinking like an attacker.
You legally break into systems to find weaknesses before real attackers do.
People who do this professionally are called penetration testers.

## Defensive Security
Defensive security is about protecting systems.
You monitor alerts, detect threats and respond to incidents.
SOC analysts do this every single day.

## Search Skills

### Google Dorking
Search engines are the most underused tool in security research.
Knowing how to search properly saves hours of work.

"exact phrase" — finds exact words together
site:example.com — searches only within that website
filetype:pdf — finds specific file types
-word — excludes a word from results
example: pyramids -tourists — shows everything about pyramids excluding tourists

### Shodan
A search engine for internet connected devices.
Finds servers, cameras, routers and industrial systems exposed online.
Really useful during penetration tests to see what a target is running.

Filters I learned:
country:PK — filter results by country
port:22 — filter by open port
hostname:example.com — filter by hostname

### VirusTotal
Scans files and URLs against 70+ antivirus engines at once.
You submit a suspicious file and it tells you how many engines flagged it.
Blue teamers use this constantly when investigating suspicious files.

### CVE and CVSS
CVE — every known vulnerability gets a unique ID like CVE-2024-1337.
CVSS — a score from 0 to 10 showing how dangerous that vulnerability is.
Higher score means fix it first.
ExploitDB has the actual exploit code for most CVEs.

### Man Pages
Every Linux command has built in documentation.
man nc — opens full manual for netcat
man nmap — opens full manual for nmap
First place to check before searching Google.

### GitHub for Security Research
Researchers publish CVE proof of concepts and tools on GitHub.
Searching a CVE number directly finds analysis and working exploits fast.
But not every PoC is reliable — some are broken or malicious on purpose.
Always verify before running anything you find.