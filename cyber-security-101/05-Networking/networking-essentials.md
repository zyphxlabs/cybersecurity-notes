# Networking Essentials
## DHCP
- Automatically gives your device IP, gateway, DNS when you connect
- Runs on UDP — server port 67, client port 68
- Four steps called DORA — Discover, Offer, Request, Acknowledge
- Before IP assigned client sends from 0.0.0.0 to 255.255.255.255
- Broadcasts to ff:ff:ff:ff:ff:ff at Layer 2 — no MAC info yet
## ARP
- Resolves IP address to MAC address on local network
- ARP Request — broadcast "who has IP x.x.x.x?"
- ARP Reply — target responds with its MAC
- Sits between Layer 2 and 3
## NAT
- One public IP shared by many private devices
- Router keeps translation table — rewrites source IP and port on every packet
- Your device sends from 192.168.0.1:15401 — internet sees 212.3.4.5:19273
## Routing Protocols
- OSPF — builds full network map, picks shortest path
- EIGRP — Cisco only, considers bandwidth and delay
- BGP — connects ISPs together, backbone of internet
- RIP — counts hops only, used in small networks
## ICMP
- Used for diagnostics only — not data transfer
- `ping <target> -c 4` — sends Echo Request Type 8, expects Echo Reply Type 0
- `traceroute <target>` Linux / `tracert <target>` Windows
- traceroute increments TTL each time — router at 0 replies with Time Exceeded Type 11
- `* * *` means that router did not reply
## Key Numbers
- DHCP server UDP 67 / client UDP 68
- Echo Request Type 8 / Echo Reply Type 0 / Time Exceeded Type 11
- Broadcast IP 255.255.255.255 / Broadcast MAC ff:ff:ff:ff:ff:ff
