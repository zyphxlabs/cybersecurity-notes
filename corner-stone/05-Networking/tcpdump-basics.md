## Tcpdump Basics

Tcpdump is basically a command line packet capture tool for linux it captures live traffic straight off the network and can also read pcap files that were saved earlier it works great alongside wireshark like you capture with tcpdump and analyze visually in wireshark

## Basic Options

- -i eth0 listen on a specific interface
- -i any listen on all interfaces
- -w file.pcap save the capture to a file
- -r file.pcap read from a saved file
- -c 10 capture only 10 packets then stop
- -n dont resolve ips
- -nn dont resolve ips or ports
- -v or -vv gives more detail in the output

## Output Options

- -q brief output
- -e shows mac addresses
- -A shows the data in ascii
- -xx shows the data in hex
- -X shows the data in both hex and ascii

## Filtering

You can filter traffic a bunch of ways like host 1.1.1.1 filters by ip src host 1.1.1.1 filters by source ip only and dst host 1.1.1.1 filters by destination ip only same logic applies to ports port 53 filters by port src port 53 by source port and dst port 53 by destination port you can also filter by protocol using tcp udp or icmp and even filter by size using greater 100 for packets over 100 bytes or less 100 for packets under 100 bytes

## Logical Operators

- and both conditions must be true
- or either condition being true is enough
- not the condition must not be true

## TCP Flags

Filtering tcp flags looks a bit weird at first tcp[tcpflags] == tcp-syn matches only syn packets tcp[tcpflags] & tcp-syn != 0 matches packets that have at least the syn flag set even if other flags are there too and tcp[tcpflags] & (tcp-syn|tcp-ack) != 0 matches packets that have either syn or ack set

## Quick Examples

- tcpdump -i any tcp port 22 captures ssh traffic
- tcpdump host example.com -w out.pcap saves traffic to a file
- tcpdump -r file.pcap src host 1.1.1.1 -n reads a file and filters by source ip
- tcpdump -r file.pcap -n | wc reads a file and counts the packets