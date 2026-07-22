## OSI Model

Osi model is basically 7 layers that explain how network communication actually works from one device to another. There is a memory trick to remember all layers from bottom to top which is please do not throw spinach pizza away

- Layer 1 Physical — cables antennas electrical and optical signals
- Layer 2 Data Link — mac addresses ethernet wifi same network communication
- Layer 3 Network — ip addresses routing between different networks
- Layer 4 Transport — tcp and udp end to end communication port numbers
- Layer 5 Session — establishes and maintains sessions between applications
- Layer 6 Presentation — encoding encryption compression ascii jpeg mime
- Layer 7 Application — http ftp dns smtp imap basically what the user sees

## TCP/IP Model

This one is more like the practical version of osi model and it only has 4 layers instead of 7. Application layer combines osi layers 5 6 and 7 into one. Transport layer is same as osi layer 4. Internet layer is same as osi layer 3. Link layer is same as osi layer 2. So basically its just osi model but simplified for real use

## IP Addresses

Every device on a network needs its own unique ip so it can talk to other devices. Ipv4 is 32 bits and made of 4 octets each one going from 0 to 255 like 192.168.1.1. Ipv6 was created because ipv4 addresses started running out

Private ip ranges are the ones that cant be reached from the internet directly

- 10.0.0.0 to 10.255.255.255
- 172.16.0.0 to 172.31.255.255
- 192.168.0.0 to 192.168.255.255

Network address is the first ip in the range like 192.168.1.0 and broadcast address is the last one like 192.168.1.255. When we say subnet /24 it means first 24 bits are fixed and we get 255 usable addresses

To check our own ip we use ipconfig on windows and ifconfig or ip a s on linux

## Routing

Router is the thing that forwards packets between different networks and it works at layer 3 which means it looks at the ip address to decide the best path forward. A packet usually passes through multiple routers before it reaches its actual destination. Nat is what allows our private ip to access the internet by using a public ip on our behalf

## UDP

Udp is connectionless which means there is no handshake and no confirmation that the data actually arrived. Its fast but unreliable so it gets used in things like video calls gaming and dns where speed matters more than perfect delivery. It still uses port numbers to identify which process the data belongs to and ports go from 1 to 65535

## TCP

Tcp is connection oriented so it has to establish a connection first before sending any data. Its reliable because every packet gets a sequence number and the receiver has to send an acknowledgement back. The way it establishes connection is through three way handshake syn then syn-ack then ack

## Encapsulation

Encapsulation is basically each layer adding its own header to the data before passing it further down. So application data goes to transport layer and gets a tcp or udp header added making it a segment. That segment goes to network layer and gets an ip header added making it a packet. Then that packet goes to data link layer and gets an ethernet header and trailer added making it a frame. On the receiving end this whole process happens in reverse to get back the original data

## Telnet

Telnet is an old protocol used for remote terminal connection and it can actually be used to connect to any open tcp port not just terminals

- telnet IP 7 — connect to echo server
- telnet IP 13 — connect to daytime server
- telnet IP 80 — connect to web server

Its not secure at all because everything gets sent as plain text so ssh is used instead nowadays