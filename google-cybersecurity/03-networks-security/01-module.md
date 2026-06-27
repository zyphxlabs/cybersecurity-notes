## What is a Network

A network is basically just a group of connected devices so like at home your laptop phone smart fridge all connected together and in office its workstations printers servers all talking to each other. Devices find each other using unique addresses called IP address and MAC address. There are mainly  two types of networks

- LAN (Local Area Network)  the small area like home office or school
- WAN (Wide Area Network)  the large area like a city state or country you can think of the internet itself as one big WAN

## Network Devices

A hub is a device that just blasts information to every single device on the network like a radio tower sending signal to anyone tuned in and because of this it is actually vulnerable to eavesdropping so modern networks do not really use them anymore. A switch is smarter than a hub because it only sends data to the device it is actually meant for so it is more secure and improves performance. Then there is the router which connects multiple networks together so when your computer wants to talk to a device on a completely different network the data goes to your router then to the other network router then finally to the destination. A modem is what connects your router to the internet basically it brings internet access into your LAN. All these things are physical hardware but cloud service providers also offer virtualization tools which are just software versions of all these devices and they save cost and scale easily

## Cloud Computing

Cloud computing is when instead of owning and managing all your own servers and hardware you just use remote servers hosted on the internet. Companies are moving to this because it saves money and removes the headache of managing physical devices. A cloud network stores everything in remote data centers and you access it through the internet. CSPs give three main types of services

- SaaS (Software as a Service)  here software you use remotely without hosting it yourself
- IaaS (Infrastructure as a Service) is virtual computers storage and containers you configure through the CSP
- PaaS (Platform as a Service) are tools for developers to build custom applications in the cloud

When a company uses both cloud and their own on-premise setup it is called a hybrid cloud environment and when they use multiple cloud providers it is called multi-cloud. Most organizations do hybrid to reduce costs while keeping some control. Cloud is attractive because of three things which are reliability meaning services stay available consistently and cost because companies do not have to buy and manage their own hardware and scalability because you only pay for what you need when you need it instead of buying equipment for a spike that might not last

## Data Packets

When devices communicate across a network data travels in pieces called data packets. Think of it like sending a physical letter where the envelope has the destination address and return address and inside is the actual message. A packet has a header which contains the destination IP address and MAC address and the protocol number telling the receiver what to do with it then there is the body which is the actual message and finally a footer which signals the packet is done. Bandwidth is how much data a device receives every second and speed is how fast packets are received if either of these look irregular it could actually be a sign of an attack. Packet sniffing is when someone captures and inspects these packets moving across the network

## TCP/IP Model

TCP/IP stands for Transmission Control Protocol and Internet Protocol and it is basically the standard model for how network communication works. TCP is what allows two devices to form a connection and stream data making sure packets reach the right place. IP is what handles the addressing and routing of those packets as they travel. It has four layers

- Network Access Layer  that deals with creating data packets and transmitting them across physical hardware like cables switches and modems
- Internet Layer this is  where IP addresses get attached to packets so devices know where the sender and receiver are and also handles how networks connect to each other
- Transport Layer is the one that controls the flow of traffic permits or denies communication and handles error control to make sure data flows smoothly
- Application Layer  is  responsible to determine how packets interact with receiving devices and handles things like file transfers and email

## IP and MAC Addresses

An IP address is a unique string of characters that identifies where a device is on the internet. IPv4 addresses are four numbers separated by a decimal point and these started running out as the internet grew so IPv6 was made which is 32 characters long and allows way more devices to connect. Public IP addresses are assigned by your ISP and are visible to the internet so all devices in one home or network share the same public IP. Private IP addresses are only visible within your local network so your devices at home can talk to each other using private addresses that the rest of the internet cannot see. MAC address is a unique alphanumeric identifier assigned to each physical device and when a switch receives a packet it reads the MAC address and uses a MAC address table like an address book to figure out which port to send it to

## OSI Model

The OSI model is a more detailed version of TCP/IP with 7 layers instead of 4 and security professionals use it to pinpoint exactly where something went wrong or where an attack happened. Going from top to bottom

- Layer 7 Application — where users interact with the network through browsers and apps using protocols like HTTP HTTPS DNS SMTP
- Layer 6 Presentation — translates and encrypts data for example SSL encryption for HTTPS happens here
- Layer 5 Session — manages the connection between two devices handles authentication reconnection and checkpoints during transfer
- Layer 4 Transport — delivers data between devices controls speed and breaks data into segments TCP and UDP work here
- Layer 3 Network — routes data packets between networks using IP addresses this is where routers operate
- Layer 2 Data Link — organizes sending and receiving within a single network where switches and network interface cards live
- Layer 1 Physical — actual physical hardware like cables hubs modems and converts data into 0s and 1s to travel through wires

## IP Packets and IPv4 vs IPv6

An IPv4 packet has two parts the header and the data. The header is between 20 to 60 bytes and contains all the routing information and the data section can go up to 65535 bytes total. The header has 13 fields like source IP destination IP TTL which prevents packets from looping forever by counting down each time it passes a router and dropping the packet when it hits zero and protocol field which tells the receiver what to do with the data. IPv4 addresses are four decimal numbers separated by periods allowing up to 4.3 billion addresses which ran out as the internet grew. IPv6 is eight hexadecimal numbers separated by colons spanning 16 bytes allowing up to 340 undecillion addresses. IPv6 also has a simpler header layout and offers more efficient routing and fixes private address collision issues that happen in IPv4