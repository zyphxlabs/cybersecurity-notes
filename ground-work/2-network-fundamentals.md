# Network Fundamentals

## What is Networking
A network is two or more devices connected together to share data.
The internet is just a massive network of networks.

## IP Addresses
Every device on a network has an IP address.
IPv4 looks like this: 192.168.1.1
IPv6 is longer — created because we ran out of IPv4 addresses.

Private IP ranges (not reachable from internet):
192.168.0.0 — 192.168.255.255
10.0.0.0 — 10.255.255.255
172.16.0.0 — 172.31.255.255

## MAC Addresses
Every network device has a MAC address burned into it.
It looks like this: a4:c3:f0:85:ac:2d
MAC addresses work at Layer 2. IP addresses work at Layer 3.

## OSI Model
7 layers. Each layer has one job.

Layer 7 — Application: HTTP, DNS, FTP. What the user sees.
Layer 6 — Presentation: Encryption and formatting. TLS lives here.
Layer 5 — Session: Manages connections between devices.
Layer 4 — Transport: TCP vs UDP. Port numbers live here.
Layer 3 — Network: IP addresses. Routers work here.
Layer 2 — Data Link: MAC addresses. Switches work here.
Layer 1 — Physical: Cables and hardware.

Memory trick bottom to top: Please Do Not Throw Sausage Pizza Away

## TCP vs UDP
TCP — reliable, confirms delivery, uses 3 way handshake.
UDP — fast, no confirmation, no handshake.

3 Way Handshake:
SYN → SYN-ACK → ACK
Client says hello. Server confirms. Client acknowledges. Done.

## Packets and Frames
Data is broken into small chunks called packets before sending.
Each packet travels independently and gets reassembled at destination.
Frames work at Layer 2 — they carry packets across a local network.

## Common Ports
22  — SSH
23  — Telnet (insecure)
53  — DNS
80  — HTTP
443 — HTTPS
3389 — RDP

## LAN
Local Area Network — devices connected in one location like a home or office.
Switch connects devices inside a LAN.
Router connects the LAN to the internet.

## Extending Networks
VPN — encrypts your traffic and hides your real IP address.
Firewall — sits between network and internet, blocks or allows traffic by rules.
