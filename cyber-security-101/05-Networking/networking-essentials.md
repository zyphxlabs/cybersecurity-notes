# Networking Essentials
## DHCP
Automatically gives your device IP, gateway, DNS when you connect.
Runs on UDP — server port 67, client port 68.
DORA: Discover → Offer → Request → Acknowledge
Before IP assigned — client sends from 0.0.0.0 to 255.255.255.255
## ARP
Resolves IP to MAC address on local network.
Request — broadcast "who has this IP?"
Reply — target sends back its MAC
## NAT
One public IP shared by many private devices.
Router keeps translation table — rewrites source IP:port on every packet.
## Routing Protocols
- OSPF — shortest path, full network map
- EIGRP — Cisco only, bandwidth + delay
- BGP — connects ISPs, backbone of internet
- RIP — hop count only, small networks
## ICMP
Diagnostics only — not data transfer.
ping — Echo Request Type 8, Echo Reply Type 0
traceroute — increments TTL, routers reply with Time Exceeded Type 11
`* * *` means router did not reply
## Key Numbers
- DHCP server UDP 67 / client UDP 68
- Echo Request Type 8 / Echo Reply Type 0
- Time Exceeded Type 11
- Broadcast IP 255.255.255.255 / MAC ff:ff:ff:ff:ff:ff
