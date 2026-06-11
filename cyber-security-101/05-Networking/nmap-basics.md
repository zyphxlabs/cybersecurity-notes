# Nmap Basics
## What It Is
- Network scanner — finds live hosts and open ports
- Can detect OS, service versions, and running software
- Run with sudo for full features
## Host Discovery
- `-sn` — ping scan, find live hosts only
- `-sL` — list targets without scanning
- Local network — uses ARP requests
- Remote network — uses ICMP, TCP SYN/ACK
## Port Scanning
- `-sT` — TCP connect scan, full three-way handshake
- `-sS` — SYN scan, stealth, only sends SYN never completes handshake
- `-sU` — UDP scan
- `-F` — fast mode, top 100 ports only
- `-p 80,443` — scan specific ports
- `-p 1-1024` — scan port range
- `-p-` — scan all 65535 ports
- `-Pn` — treat all hosts as online, skip host discovery
## Service and OS Detection
- `-sV` — detect service versions
- `-O` — detect operating system
- `-A` — OS + version + traceroute all in one
## Timing Templates
- `-T0` paranoid — very slow, 9 hours for 100 ports
- `-T1` sneaky — slow, evades IDS
- `-T2` polite — slower than normal
- `-T3` normal — default
- `-T4` aggressive — faster, good networks
- `-T5` insane — very fast, may miss things
- `--min-rate 100` / `--max-rate 100` — control packets per second
- `--host-timeout` — skip slow hosts after set time
## Output
- `-oN file.txt` — normal readable output
- `-oX file.xml` — XML format
- `-oG file.gnmap` — grepable format
- `-oA basename` — save all three formats at once
- `-v` / `-vv` — verbose output
- `-d` / `-d9` — debug output
## Target Formats
- `192.168.1.1` — single IP
- `192.168.1.1-10` — IP range
- `192.168.1.0/24` — full subnet
- `example.com` — hostname
