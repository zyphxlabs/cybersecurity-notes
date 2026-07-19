## Nmap Basics

Nmap is basically a network scanner that finds live hosts and open ports on a network you can run it with sudo to unlock full features like os detection it also detects service versions and running software so you know exactly whats up on a machine

## Host Discovery

- -sn ping scan finds live hosts only doesnt scan ports
- -sL just lists the targets without actually scanning them

On a local network it uses arp requests to find hosts but on a remote network it switches to icmp or tcp syn/ack since arp doesnt work outside the local segment

## Port Scanning

- -sT tcp connect scan completes the full three way handshake
- -sS syn scan the stealthy one sends syn but never finishes the handshake so its quieter
- -sU udp scan
- -F fast mode only checks top 100 ports
- -p 80,443 scan specific ports
- -p 1-1024 scan a port range
- -p- scan literally all 65535 ports
- -Pn treats all hosts as online and skips host discovery completely useful when host discovery is being blocked

## Service and OS Detection

- -sV detects service versions running on open ports
- -O detects the operating system
- -A combines os detection version detection and traceroute all in one scan

## Timing Templates

Nmap has timing templates from t0 to t5 and basically the lower the number the slower and sneakier the scan is t0 paranoid is super slow like 9 hours for 100 ports made to dodge detection t1 sneaky is slow too and evades ids t2 polite is slower than normal so it doesnt hog bandwidth t3 normal is just the default speed t4 aggressive is faster and works fine on good stable networks and t5 insane is the fastest one but it might miss stuff because its rushing

You can also control speed manually with --min-rate 100 or --max-rate 100 to set packets per second and --host-timeout to skip hosts that are taking too long to respond

## Output

- -oN file.txt normal readable output
- -oX file.xml xml format
- -oG file.gnmap grepable format
- -oA basename saves all three formats together at once
- -v or -vv gives verbose output
- -d or -d9 gives debug output for deeper troubleshooting

## Target Formats

- 192.168.1.1 single ip
- 192.168.1.1-10 ip range
- 192.168.1.0/24 full subnet
- example.com hostname