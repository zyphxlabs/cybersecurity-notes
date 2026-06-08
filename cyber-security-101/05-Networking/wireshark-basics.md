# Wireshark Basics
## What It Is
- Network packet analyser — captures and reads traffic
- Works on live traffic and PCAP files
- Not an IDS — only reads packets, never modifies them
## Interface
- Packet List Pane — list of all packets
- Packet Details Pane — full breakdown of selected packet
- Packet Bytes Pane — hex and ASCII of selected packet
- Display Filter Bar — filter what you see
- Status Bar — interface and packet count
## Packet Layers
- Layer 1 — physical frame info
- Layer 2 — source and destination MAC
- Layer 3 — source and destination IP
- Layer 4 — TCP or UDP, ports
- Layer 5 — application protocol and data
## Useful Features
- Merge PCAPs — File → Merge
- Mark Packets — highlight packets, lost when file closes
- Packet Comments — notes saved inside the file
- Export Objects — extract files from HTTP, SMB, FTP streams
- Follow Stream — shows full readable conversation
- Apply as Column — add any field to packet list view
- Expert Info — Analyse → Expert Information
## Expert Info Colours
- Blue — normal traffic
- Cyan — app error codes
- Yellow — unusual errors
- Red — malformed packets
## Display Filters
- `http` — HTTP only
- `dns` — DNS only
- `arp` — ARP only
- `tcp.port == 80` — by port
- `ip.addr == 192.168.1.1` — by IP