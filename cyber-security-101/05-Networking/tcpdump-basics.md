# Tcpdump Basics
## What It Is
- Command line packet capture tool for Linux
- Captures live traffic and reads PCAP files
- Works great alongside Wireshark
## Basic Options
- `-i eth0` — listen on specific interface
- `-i any` — listen on all interfaces
- `-w file.pcap` — save to file
- `-r file.pcap` — read from file
- `-c 10` — capture only 10 packets
- `-n` — don't resolve IPs
- `-nn` — don't resolve IPs or ports
- `-v` / `-vv` — more detail in output
## Output Options
- `-q` — brief output
- `-e` — show MAC addresses
- `-A` — show data in ASCII
- `-xx` — show data in hex
- `-X` — show data in hex and ASCII
## Filtering
- `host 1.1.1.1` — by IP
- `src host 1.1.1.1` — by source IP
- `dst host 1.1.1.1` — by destination IP
- `port 53` — by port
- `src port 53` — by source port
- `dst port 53` — by destination port
- `tcp` / `udp` / `icmp` — by protocol
- `greater 100` — packets over 100 bytes
- `less 100` — packets under 100 bytes
## Logical Operators
- `and` — both must be true
- `or` — either is true
- `not` — must not be true
## TCP Flags
- `tcp[tcpflags] == tcp-syn` — only SYN
- `tcp[tcpflags] & tcp-syn != 0` — at least SYN
- `tcp[tcpflags] & (tcp-syn|tcp-ack) != 0` — SYN or ACK
## Quick Examples
- `tcpdump -i any tcp port 22` — SSH traffic
- `tcpdump host example.com -w out.pcap` — save to file
- `tcpdump -r file.pcap src host 1.1.1.1 -n` — read and filter
- `tcpdump -r file.pcap -n | wc` — count packets
