# Nmap Cheatsheet
## Host Discovery
- `nmap -sn 192.168.1.0/24` — find live hosts
- `nmap -sL 192.168.1.0/24` — list targets without scanning
## Port Scans
- `nmap -sT <target>` — TCP connect scan
- `nmap -sS <target>` — SYN stealth scan
- `nmap -sU <target>` — UDP scan
- `nmap -F <target>` — fast scan top 100 ports
- `nmap -p 80,443 <target>` — specific ports
- `nmap -p 1-1024 <target>` — port range
- `nmap -p- <target>` — all ports
- `nmap -Pn <target>` — skip host discovery
## Detection
- `nmap -sV <target>` — service version
- `nmap -O <target>` — OS detection
- `nmap -A <target>` — OS + version + traceroute
## Timing
- `nmap -T0 <target>` — paranoid
- `nmap -T1 <target>` — sneaky
- `nmap -T2 <target>` — polite
- `nmap -T3 <target>` — normal
- `nmap -T4 <target>` — aggressive
- `nmap -T5 <target>` — insane
## Output
- `nmap -oN file.txt <target>` — normal
- `nmap -oX file.xml <target>` — XML
- `nmap -oG file.gnmap <target>` — grepable
- `nmap -oA basename <target>` — all formats
## Combine Options
- `nmap -sS -sV -O -T4 -p- <target>` — full scan
- `nmap -sS -F -T4 <target>` — quick stealth scan