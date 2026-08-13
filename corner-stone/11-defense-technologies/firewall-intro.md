## What a Firewall Actually Does
Kinda like a security guard standing outside a mall or a bank checking who comes in and who goes out, a firewall does the same thing but for network traffic. Theres a constant flow of data moving between our devices and the internet, and without something checking that traffic anyone could sneak something malicious through without getting noticed. A firewall inspects incoming and outgoing traffic on a network or device and decides what gets through based on rules you give it. Anything trying to enter or leave has to pass through the firewall first, and it gets allowed or denied depending on how the rules are set up. Modern firewalls go way past just basic rule matching too, a lot of them add extra protective functionality on top

## Types of Firewalls
Different firewalls operate at different layers of the osi model and each type serves a different purpose

Stateless firewalls work at layer 3 and 4, filtering purely based on predetermined rules with zero memory of previous connections. Every packet gets checked fresh against the rule set regardless of whether its part of an already established legit connection. This makes them fast since theres no state to track, but it also means if it denies a few packets from some source it wont automatically keep denying future ones from that same source, itll just re-evaluate every new packet against the rules from scratch every single time

Stateful firewalls also work at layer 3 and 4 but go further by actually tracking connection history in a state table. If it allows some packets from a source it remembers that connection and lets future packets from it through automatically without re-inspecting each one. Same logic applies to denials, once it denies packets from a source it remembers that too and keeps denying future ones from the same connection. This adds a real layer of context stateless firewalls just dont have

Proxy firewalls, also called application level gateways, work up at layer 7 and actually inspect the full content of packets instead of just headers. They sit as a middleman between the internal network and the internet, forwarding requests after inspecting them and masking the internal ip with their own for anonymity. Since they see actual content they can apply content filtering policies on top of just allow or deny

Next-gen firewalls (ngfw) are the most advanced type, spanning layer 3 all the way to layer 7. They do deep packet inspection, come with a built in intrusion prevention system to block malicious activity live, use heuristic analysis to catch attack patterns before they even land, and can decrypt and inspect ssl/tls traffic while correlating everything against threat intel feeds for smarter decisions

Quick comparison of the four

- stateless — basic filtering, no connection memory, great for high speed networks needing fast processing
- stateful — recognizes traffic patterns, supports more complex rules, actively monitors connections
- proxy — inspects actual packet content, offers content filtering and app control, can decrypt and inspect ssl/tls
- ngfw — advanced threat protection, built in ips, heuristic anomaly detection, ssl/tls decryption and inspection

## Firewall Rule Components
A firewall rule is built from a handful of core fields

- source address — the ip the traffic is coming from
- destination address — the ip the traffic is headed to
- port — which port the traffic is using
- protocol — what protocol is being used for the communication
- action — what actually happens once traffic matches this rule
- direction — whether the rule applies to incoming or outgoing traffic

## Types of Actions
Allow just means traffic matching the rule gets permitted through. Example rule allowing all outgoing http traffic from a subnet

| Action | Source | Destination | Protocol | Port | Direction |
|--------|--------|-------------|----------|------|-----------|
| Allow | 192.168.1.0/24 | Any | TCP | 80 | Outbound |

Deny means traffic matching the rule gets blocked outright, these are core to actually reducing a networks attack surface by shutting down specific unwanted traffic. Example blocking inbound ssh to a critical server

| Action | Source | Destination | Protocol | Port | Direction |
|--------|--------|-------------|----------|------|-----------|
| Deny | Any | 192.168.1.0/24 | TCP | 22 | Inbound |

Forward redirects traffic to a different network segment, this only really applies to firewalls acting as gateways or doing routing between segments. Example forwarding incoming http traffic to an internal web server

| Action | Source | Destination | Protocol | Port | Direction |
|--------|--------|-------------|----------|------|-----------|
| Forward | Any | 192.168.1.8 | TCP | 80 | Inbound |

## Rule Directionality
Inbound rules only apply to incoming traffic, like allowing incoming http on a public facing web server

Outbound rules only apply to outgoing traffic, like blocking all outbound smtp except from the actual mail server

Forward rules push specific traffic to somewhere else inside the network, like forwarding incoming http requests to wherever the actual web server lives internally

## Windows Firewall (Windows Defender Firewall)
Windows ships with its own built in firewall covering the basics, creating rules and allowing or denying specific programs or custom traffic. It works off network profiles, and windows automatically detects which one applies based on network location awareness

- private networks — settings meant for a trusted network like home
- public/guest networks — settings meant for untrusted networks like a coffee shop, usually locked down tighter, blocking most incoming connections by default while still allowing whatever outgoing stuff is actually needed

Each profile can have totally different settings applied independently, so a rule allowing something on your private network wont automatically apply while youre on public wifi. You can also allow or block specific installed apps per profile individually instead of an all or nothing approach, and thereas always a restore defaults option if things get messed up

Custom rules let you get way more specific, like blocking all outbound traffic on ports 80 and 443, which would completely kill regular web browsing since basically every site runs on one of those two ports. Building a custom rule generally walks through picking inbound or outbound, selecting which programs it applies to, setting the protocol and port, defining scope for source and destination ip, picking the action like block or allow, choosing which network profiles it applies to and finally naming it. Once created it shows up in the outbound or inbound rules list and can be tested immediately by trying to hit a site and confirming its actually blocked

## Linux Firewalls
Netfilter is the underlying framework built into the linux kernel handling the core firewall functionality, packet filtering nat and connection tracking. Its the foundation basically every linux firewall tool is built on top of

- iptables — the most widely used one across distros, built directly on netfilter
- nftables — the newer successor to iptables with improved filtering and nat capability, still netfilter based
- firewalld — also netfilter based but works differently with predefined zone based configurations instead of raw rule chains

ufw (uncomplicated firewall) exists specifically to simplify all this, giving a much friendlier command syntax instead of dealing with raw iptables complexity directly. Under the hood it just configures iptables for you based on the simpler commands you give it

Checking current status

```
sudo ufw status
```

Enabling it

```
sudo ufw enable
```

Swap enable for disable to turn it back off. Setting a default policy, like allowing all outgoing traffic by default unless a specific rule overrides it for something

```
sudo ufw default allow outgoing
```

Same idea works for incoming by swapping outgoing for incoming. Denying traffic on a specific port, like blocking inbound ssh

```
sudo ufw deny 22/tcp
```

Listing all active rules with numbers so you can reference them later

```
sudo ufw status numbered
```

Deleting a specific rule by its number from that list

```
sudo ufw delete 2
```

Which utility actually makes sense to use on a given system really comes down to familiarity and whatever the specific requirements are, ufw is great for quick simple setups while iptables or nftables give way more granular control when actually needed