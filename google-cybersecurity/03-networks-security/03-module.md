## Why Network Security Matters

Networks are constantly at risk and attackers can get in through malware spoofing or packet sniffing and can also just disrupt everything by flooding the network with traffic. A real example of why this matters is the Home Depot attack in 2014 where a group of hackers compromised and infected their servers with malware and by the time admins shut it down the hackers had already stolen credit and debit card information of over 56 million customers. Attacks can leak confidential information damage reputation lose customers and cost the organization a lot of money and time to fix

## Network Interception and Backdoor Attacks

Network interception attacks work by getting in between traffic and either stealing data or messing with it. Attackers use hardware or software tools to capture packets in transit which is packet sniffing and they can also alter those packets like changing the bank account number in a transaction to one they control. Backdoor attacks are when someone uses a weakness that was intentionally left in a system by programmers or admins to bypass normal access control. These were meant for troubleshooting but attackers can also install their own backdoors after breaking in to keep persistent access. Once inside through a backdoor they can install malware run a DoS attack steal data or mess with security settings leaving the system open to even more attacks. The impact of these attacks on an organization can be financial because operations going offline means no revenue and ransomware costs are huge or reputational because if people find out you got attacked they stop trusting you or even public safety if the target is something like a power grid or military communication system

## DoS and DDoS Attacks

A DoS attack basically floods a network or server with so much traffic that it crashes or cannot respond to real users anymore. A DDoS attack is just a bigger version of that where instead of one device flooding the target multiple devices and servers from different locations are all sending traffic at once which makes it much harder to stop. There was a real DDoS attack on October 21 2016 where a group of university students had built a botnet originally to attack gaming servers and then posted the code online so anyone could use it. Some cybercriminals took that code and used it to attack a major DNS service provider by sending tens of millions of DNS requests at 7:00 a.m. which shut down the DNS system completely. Because the DNS was down none of the websites using that provider could be reached and outages hit across North America and Europe. The service was restored after only two hours and when the criminals sent follow-up waves the DNS company was ready and mitigated them. A botnet by the way is just a bunch of computers infected with malware all controlled by one person called the bot-herder

Three common DoS attacks at the network level

- SYN flood attack — floods the server with SYN packets which are the first step of the TCP handshake. The server keeps ports open waiting for the final ACK that never comes and when the SYN requests outnumber available ports the server gets overwhelmed and cannot function
- ICMP flood attack — attacker keeps sending ICMP packets to the server forcing it to keep responding until all bandwidth is used up and it crashes
- Ping of death — attacker sends one oversized ICMP packet bigger than 64 kilobytes which is the maximum allowed size for a correctly formed ICMP packet and this single oversized packet overloads and crashes the system

## Packet Sniffing

Packet sniffing is when someone uses software tools to watch data as it moves across a network. Security analysts use it legitimately to investigate incidents and debug issues but malicious actors also use it to read data that was never meant for them. Packets carry a header with IP and MAC addresses and a body that can contain names dates of birth financial info and credit card numbers so there is a lot of valuable stuff to steal. Passive packet sniffing is when the attacker just reads packets in transit without touching them like a postal worker reading your mail while still delivering it. Active packet sniffing is when they actually manipulate the packets in transit like injecting protocols to redirect them or changing the content inside the packet. To protect against this use a VPN so even if someone intercepts the traffic they cannot decode it make sure websites use HTTPS with SSL/TLS encryption and avoid using unprotected public WiFi at places like coffee shops and airports because those networks have no encryption and anyone on them can see all your data

## tcpdump

tcpdump is a command-line network protocol analyzer that is lightweight uses little memory and low CPU runs on Linux and macOS and uses the open-source libpcap library. It captures packets and prints out readable information directly in the terminal including timestamp source IP source port destination IP and destination port. It is used to monitor traffic patterns troubleshoot performance issues detect malicious traffic and locate unauthorized activity on the network. But attackers can also use tools like this to capture sensitive data like usernames and passwords so understanding how it works is important for both offense and defense

## IP Spoofing and Interception Attacks

IP spoofing is when an attacker changes the source IP address in a data packet to pretend they are an authorized system and get past firewall rules. After sniffing the network they learn the IP and MAC addresses of trusted devices and then impersonate them. There are a few common attacks that use this

- On-path attack the attacker puts themselves in the middle of a connection between two trusted devices and intercepts or alters the data. Can also intercept DNS lookups and redirect a domain to a malicious IP address. Protection is encrypting data in transit using TLS
- Replay attack the attacker intercepts a valid data packet and either delays it causing connection issues or replays it later to impersonate the authorized user who originally sent it
- Smurf attack so in this attacker sniffs an authorized user's IP address and floods it with ICMP packets. The spoofed packet hits the broadcast address and gets sent to every device on the network overwhelming everything and causing a DoS. NGFWs can detect oversized broadcasts and stop this

To protect against IP spoofing firewalls should be configured to reject any incoming traffic from the internet that has the same IP address as the internal private network because those devices should already be on the local network not coming from outside