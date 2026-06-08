# Networking Secure Protocols
## TLS
- Adds confidentiality, integrity, authenticity to existing protocols
- HTTP, SMTP, POP3, IMAP become HTTPS, SMTPS, POP3S, IMAPS
- SSL came first in 1995 — TLS replaced it in 1999 — TLS 1.3 current version
- Server gets a TLS certificate signed by a Certificate Authority (CA)
- Self-signed certificate cannot prove authenticity — no third party confirmed it
- HTTPS connection steps: TCP handshake → TLS handshake → HTTP data
- Without TLS all traffic readable in Wireshark as plain text
## Secure Port Numbers
| Protocol | Insecure Port | Secure Port |
|----------|--------------|-------------|
| HTTP | 80 | 443 |
| SMTP | 25 | 465 / 587 |
| POP3 | 110 | 995 |
| IMAP | 143 | 993 |
## SSH
- Replaces TELNET — all traffic encrypted instead of cleartext
- Listens on TCP port 22
- `ssh username@hostname` — connect to remote machine
- `ssh hostname -X` — connect with graphical interface support
- Supports password auth, public key auth, two-factor auth
- Protects confidentiality, integrity, prevents man-in-the-middle
- Can tunnel other protocols through SSH — VPN-like
## SFTP
- Secure file transfer over SSH — same port 22
- `sftp username@hostname` — connect
- `get filename` — download file
- `put filename` — upload file
- Not the same as FTPS
## FTPS
- FTP secured with TLS — port 990
- Needs a TLS certificate to run
- Harder to configure than SFTP — separate control and data connections
## VPN
- Connects devices or branches over internet as if on same private network
- VPN client encrypts traffic and sends through tunnel to VPN server
- Servers you visit see VPN server IP not your real IP
- Used to bypass geo-restrictions and ISP censorship
- ISP only sees encrypted traffic
- Some VPNs leak real IP — run DNS leak test to verify
- VPN is illegal in some countries — check local laws before using