# Networking Concepts

## OSI Model
7 layers that describe how network communication works.
Memory trick bottom to top: Please Do Not Throw Spinach Pizza Away

- Layer 1 Physical — cables, antennas, electrical and optical signals
- Layer 2 Data Link — MAC addresses, Ethernet, WiFi, same network communication
- Layer 3 Network — IP addresses, routing between different networks
- Layer 4 Transport — TCP and UDP, end to end communication, port numbers
- Layer 5 Session — establishes and maintains sessions between applications
- Layer 6 Presentation — encoding, encryption, compression. ASCII, JPEG, MIME
- Layer 7 Application — HTTP, FTP, DNS, SMTP, IMAP. What the user sees

## TCP/IP Model
Practical version of OSI. 4 layers.
- Application — combines OSI layers 5, 6, 7
- Transport — same as OSI layer 4
- Internet — same as OSI layer 3
- Link — same as OSI layer 2

## IP Addresses
Every device needs a unique IP to communicate on a network.
IPv4 — 32 bits, 4 octets, each 0 to 255. Example: 192.168.1.1
IPv6 — created because we ran out of IPv4 addresses.

Private IP ranges — not reachable from internet:
- 10.0.0.0 to 10.255.255.255
- 172.16.0.0 to 172.31.255.255
- 192.168.0.0 to 192.168.255.255

Network address — first IP in range. Example: 192.168.1.0
Broadcast address — last IP in range. Example: 192.168.1.255
Subnet /24 means first 24 bits fixed — 255 usable addresses.

Commands to check IP:
- Windows: `ipconfig`
- Linux: `ifconfig` or `ip a s`

## Routing
Router forwards packets between different networks.
Works at Layer 3 — inspects IP address and picks best path.
Packet passes through multiple routers to reach destination.
NAT allows private IPs to access internet through a public IP.

## UDP
Connectionless — no handshake, no confirmation of delivery.
Fast but unreliable. Good for video calls, gaming, DNS.
Uses port numbers to identify processes. Ports 1 to 65535.

## TCP
Connection oriented — must establish connection before sending data.
Reliable — every packet has sequence number, receiver sends acknowledgement.
Uses three way handshake: SYN → SYN-ACK → ACK

## Encapsulation
Each layer adds its own header to the data before passing it down.
- Application data → Transport adds TCP/UDP header → segment
- Segment → Network adds IP header → packet
- Packet → Data Link adds Ethernet header and trailer → frame
Receiving end reverses this process to extract the original data.

## Telnet
Old protocol for remote terminal connection.
Can be used to connect to any open TCP port.
- `telnet IP 7` — connect to echo server
- `telnet IP 13` — connect to daytime server
- `telnet IP 80` — connect to web server
Not secure — everything sent as plain text. Use SSH instead.