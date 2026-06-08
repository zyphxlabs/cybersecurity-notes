# Protocols Cheatsheet
## Port Numbers
| Protocol | Transport | Port |
|----------|-----------|------|
| TELNET | TCP | 23 |
| SSH | TCP | 22 |
| DNS | UDP/TCP | 53 |
| HTTP | TCP | 80 |
| HTTPS | TCP | 443 |
| FTP | TCP | 21 |
| SFTP | TCP | 22 |
| FTPS | TCP | 990 |
| SMTP | TCP | 25 |
| SMTPS | TCP | 465/587 |
| POP3 | TCP | 110 |
| POP3S | TCP | 995 |
| IMAP | TCP | 143 |
| IMAPS | TCP | 993 |
| DHCP server | UDP | 67 |
| DHCP client | UDP | 68 |
## What Each Protocol Does
- HTTP — browser to web server
- HTTPS — HTTP over TLS
- FTP — file transfer
- SFTP — file transfer over SSH
- FTPS — file transfer over TLS
- SMTP — sending email
- POP3 — download email, deletes from server
- IMAP — sync email across devices, stays on server
- DNS — resolves domain names to IP addresses
- DHCP — gives device IP, gateway, DNS automatically
- TELNET — remote terminal, cleartext, insecure
- SSH — remote terminal, encrypted, replaced TELNET
- TLS — encrypts existing protocols, adds S to name
- VPN — private encrypted tunnel over public internet
- ARP — resolves IP to MAC on local network
- NAT — many private IPs share one public IP
- ICMP — diagnostics only, used by ping and traceroute
## DNS Record Types
- A — domain to IPv4
- AAAA — domain to IPv6
- CNAME — domain to another domain
- MX — mail server for domain
## ICMP Types
- Type 8 — Echo Request (ping sends this)
- Type 0 — Echo Reply (target sends this back)
- Type 11 — Time Exceeded (traceroute uses this)