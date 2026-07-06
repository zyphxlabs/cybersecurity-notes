## Network Traffic and Network Data

Network traffic is basically the amount of data moving across a network at any point and network data is the actual data thats being transmitted between devices. In a huge org with thousands of employees sending emails at once the traffic volume gets massive so the real challenge becomes figuring out whats normal and whats not.

## Baselines

A baseline is just a reference point you compare stuff against like knowing your normal grocery spending so you notice when it spikes. In networks a baseline means knowing the normal expected behavior of systems and devices so anything that deviates from it becomes easier to catch. Its basically like knowing your normal commute traffic pattern so when theres a random jam at 2am you know something is off.

## Indicators of Compromise (IOC)

Ioc is just observable evidence that hints something bad might be happening. Like if theres a sudden huge chunk of outbound traffic leaving a host that could be a sign of data getting stolen so its worth digging into.

## Data Exfiltration

Data exfiltration is basically unauthorized transmission of data out of a system attackers do this to steal stuff like usernames passwords or intellectual property. You catch it by watching for weird traffic patterns like large amounts of data leaving somewhere it shouldnt.

## Things to Monitor On a Network

- flow analysis which is about the movement of packets protocols and ports and watching for mismatches like a protocol running on a port it normally shouldnt use since attackers do this to hide their command and control c2 traffic which is basically how they keep talking to a system theyve already hacked
- packet payload information which is the actual data inside the packet often encrypted but when its not you can catch stuff like sensitive data leaving the network which points toward exfiltration
- temporal patterns meaning normal traffic happens during expected hours like 9 to 5 so if theres a big traffic spike at 3am thats off baseline and needs checking

## NOC vs SOC

A noc is network operations center and its job is keeping the network performing well and available basically uptime and outages is their concern. A soc on the other hand is all about security detecting and responding to threats. So noc cares about the network working soc cares about the network being safe.

## Data Exfiltration Attack from Attackers Point of View

First the attacker needs initial access usually through something like phishing where they trick someone into giving up their credentials through a fake link or attachment. Once theyre in they dont just stop there they do lateral movement also called pivoting which means exploring the network quietly trying to expand their reach to other systems without getting caught. While pivoting they scope out valuable stuff like proprietary code pii or financial records by digging through file shares intranet sites code repos and similar spots. After finding the good stuff they package and shrink the data down to sneak past security controls and finally they exfiltrate it out usually to somewhere like their own email account.

## Defending Against Data Exfiltration

- prevent initial access using stuff like multi factor authentication so phishing doesnt work as easily
- monitor network activity for weird signs like logins coming from ip addresses that shouldnt be there
- keep proper asset inventory and apply the right security controls on valuable assets
- watch for signs of unusual data movement like large internal transfers large external uploads or unexpected file writes siem tools can catch and alert on these
- once detected block the attacker using firewall rules to stop the exfiltration from continuing

## Packets

A packet is the basic unit that carries info from one device to another over a network. Every time you do something online like visit a site or upload an image the data gets split into packets sent over and reassembled at the other end. Packets have three parts

- header which carries routing info like source and destination ip protocol and packet length
- payload which is the actual data being sent like the image itself
- footer which comes at the end mostly used by ethernet for error checking most protocols like ip dont even use footers

## Network Protocol Analyzers

These are basically packet sniffers tools made to capture and analyze data traffic like tcpdump wireshark and tshark. Analysts use them to catch suspicious activity but attackers can misuse them too like capturing login info off the wire.

How they actually work is packets first get grabbed through the nic which is the hardware connecting a computer to the network. Normally a nic only picks up traffic meant for it but switching it to promiscuous mode or monitoring mode for wireless lets it see everything passing by. The analyzer then takes this raw binary data and turns it into something humans can actually read.

## Packet Capture Pcap

Packet sniffing is just the act of grabbing and inspecting these packets and a packet capture or pcap is the actual file that stores all this intercepted data. You can filter pcap files down to just what matters like packets from one ip. There are different pcap formats depending on the library used

- libpcap used by unix like systems such as linux and macos tools like tcpdump use this by default
- winpcap older format made for windows not really used anymore
- npcap made by nmap commonly used on windows now
- pcapng a newer format that can capture and store data at the same time hence next gen

## Ipv4 header fields

Ipv4 has thirteen fields in its header

- version tells which ip version is used
- ihl internet header length shows length of header plus options
- tos type of service shows priority of delivery
- total length full size of the packet header and data combined
- identification flags and fragment offset all deal with fragmentation basically how a packet gets split and reassembled properly
- ttl time to live decides how long a packet survives before getting dropped stops infinite looping
- protocol tells which protocol is being used like tcp represented by number 6
- header checksum used to check if header got corrupted
- source address the sender ip
- destination address the receiver ip
- options optional field mostly used for troubleshooting not regular traffic

## Ipv6 header fields

Ipv6 is getting more common because of its huge address space it has eight fields

- version shows ipv6 is used
- traffic class same idea as tos shows priority
- flow label identifies packets belonging to the same flow
- payload length size of the data portion
- next header shows what header type comes after like tcp
- hop limit same as ttl basically
- source address sender ip
- destination address receiver ip

## Wireshark

Wireshark is an open source protocol analyzer with a gui which makes reading packet info way easier compared to staring at raw binary. It uses display filters to help you dig through huge pcap files and find exactly what you need.

Comparison operators you can use

- == or eq for equal
- != or ne for not equal
- > or gt greater than
- < or lt less than
- >= or ge greater than or equal
- <= or le less than or equal

You can also combine filters using and or or and use parentheses to group them for more complex searches.

There is also the contains operator which finds packets matching an exact string and the matches operator which uses regex patterns instead.

Some useful filter examples

- typing a protocol name like dns http ftp ssh arp telnet or icmp filters for just that protocol
- ip.addr == 172.21.224.2 filters for a specific ip whether source or destination
- ip.src == 10.10.10.10 filters by source ip only
- ip.dst == 4.4.4.4 filters by destination ip only
- eth.addr == 00:70:f4:23:18:c4 filters by mac address
- udp.port == 53 or tcp.port == 25 filters by port number

Theres also follow stream which lets you view a full conversation between two devices reassembled nicely instead of individual scattered packets useful when you wanna see the full picture of like an http exchange.

## Tcpdump

Tcpdump is a command line based protocol analyzer comes preinstalled on most linux systems and works on macos too. Since it needs elevated access you gotta run it with sudo. Basic syntax is sudo tcpdump followed by the interface option and then whatever other options or expressions you want.

Some important options

- -i picks the interface to sniff on using any grabs traffic from all interfaces
- -w saves captured packets into a pcap file instead of just printing them out
- -r reads back a saved pcap file
- -v -vv -vvv controls verbosity meaning how much detail gets printed more vs get more info
- -c controls how many packets to capture like -c 1 grabs just one packet
- -n stops tcpdump from resolving ip to hostnames and -nn also stops port name resolution this matters because resolving names can be inaccurate and can even alert an attacker through reverse dns lookups

You can combine short options together like -vn but not ones that need a value right after like -c or -r.

Expressions let you filter traffic further like using ip6 to grab only ipv6 traffic or combining conditions with and or or not for example filtering ip and port 80 together. Parentheses can group expressions too like ip and (port 80 or port 443) to prioritize what gets filtered first.

When you run a capture the output always starts with a timestamp showing hours minutes seconds and fractions which is super useful for building timelines during an investigation. After that it shows source ip and port then destination ip and port followed by protocol details like tcp flags and sequence numbers depending on verbosity.