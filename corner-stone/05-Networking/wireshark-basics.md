## Wireshark Basics

Wireshark is basically a network packet analyser it captures traffic live and can also read pcap files that were already saved its not an ids so it doesnt block or modify anything it just reads packets and shows you whats happening

## Interface

Wireshark splits its window into a few main areas the packet list pane shows the list of all captured packets the packet details pane shows the full breakdown of whichever packet you click on the packet bytes pane shows that same packet in hex and ascii below it theres the display filter bar where you type filters to narrow down what you see and the status bar at the bottom shows which interface youre on and how many packets got captured

## Packet Layers

When you click a packet it breaks down into layers layer 1 is just the physical frame info layer 2 shows the source and destination mac addresses layer 3 shows the source and destination ip layer 4 shows tcp or udp along with the ports and layer 5 is the actual application protocol and the data itself so basically the deeper you go the more specific the info gets

## Useful Features

- merge pcaps file then merge combines two capture files into one
- mark packets highlights packets you want to keep an eye on but this gets lost once you close the file
- packet comments lets you add notes that actually get saved inside the file itself
- export objects lets you pull actual files out of http smb or ftp streams
- follow stream shows the full readable conversation between two hosts instead of packet by packet
- apply as column lets you take any field from a packet and add it as its own column in the packet list
- expert info found under analyse then expert information flags anything unusual or broken automatically

## Expert Info Colours

- blue normal traffic nothing wrong
- cyan app error codes at the application level
- yellow unusual errors worth checking
- red malformed packets something is broken or corrupted

## Display Filters

- http shows only http traffic
- dns shows only dns traffic
- arp shows only arp traffic
- tcp.port == 80 filters by a specific port
- ip.addr == 192.168.1.1 filters by a specific ipS