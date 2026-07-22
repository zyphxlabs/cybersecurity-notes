## DHCP
Dhcp is basically the thing that gives your device ip gateway and dns automatically the moment you connect to a network so you dont have to set it up manually. It runs on udp where server uses port 67 and client uses port 68. The process is called dora which means discover offer request acknowledge basically the device asks for an ip the server offers one device requests it and server confirms it. Before the device even gets an ip it sends from 0.0.0.0 to 255.255.255.255 because it doesnt have an identity yet on the network

## ARP
Arp is used to find out the mac address of a device when you already know its ip on the local network. It works in two steps first is request where the device broadcasts asking who has this ip and then reply where the actual owner of that ip sends back its mac address directly

## NAT
Nat is how one public ip gets shared between a lot of private devices at home or office. The router keeps a translation table in memory and every time a packet goes out or comes in it rewrites the source ip and port so multiple devices can use the internet through a single public ip without conflict

## Routing Protocols
these protocols decide how routers find the best path to send data
- OSPF — finds shortest path and keeps a full map of the network
- EIGRP — cisco only protocol uses bandwidth and delay to decide path
- BGP — connects different isps together basically the backbone of the internet
- RIP — only counts hops used for small networks

## ICMP
Icmp is not for sending actual data its just used for diagnostics like checking if something is reachable or finding the path packets take. Ping uses echo request type 8 and gets back echo reply type 0 to confirm a device is alive. Traceroute works by increasing the ttl value each time and every router along the path replies with time exceeded type 11 until it reaches destination. When you see `* * *` in traceroute it just means that particular router chose not to reply

## Key Numbers
these are the numbers that keep showing up so better to remember them
- DHCP server UDP 67 / client UDP 68
- Echo Request Type 8 / Echo Reply Type 0
- Time Exceeded Type 11
- Broadcast IP 255.255.255.255 / MAC ff:ff:ff:ff:ff:ff