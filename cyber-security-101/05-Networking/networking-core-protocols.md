# Networking Core Protocols
## DNS
- Translates domain names to IP addresses
- UDP port 53, TCP port 53 as fallback
- A record — domain to IPv4
- AAAA record — domain to IPv6
- CNAME record — domain to another domain
- MX record — mail server for a domain
- `nslookup example.com` — look up IP of a domain
## WHOIS
- Database of every registered domain
- Shows registrant name, email, phone, address, dates
- `whois example.com` — look up domain info
- Privacy protection replaces real info with proxy details
## HTTP
- How browsers talk to web servers
- TCP port 80 HTTP / TCP port 443 HTTPS
- GET — fetch a page or file
- POST — send data to server
- PUT — create or overwrite resource
- DELETE — remove resource
## FTP
- Designed for file transfer
- TCP port 21
- RETR — download file
- STOR — upload file
- Anonymous login allowed on some servers
## SMTP
- Sends email between client and server
- TCP port 25
- HELO — start session
- MAIL FROM — sender address
- RCPT TO — recipient address
- DATA — write email body
- `.` alone on a line — end email
## POP3
- Downloads email to client and deletes from server
- Single device use only
- TCP port 110
- STAT — message count and size
- LIST — list all messages
- RETR 3 — get message 3
- DELE 3 — delete message 3
## IMAP
- Syncs email across multiple devices — keeps on server
- TCP port 143
- SELECT inbox — open mailbox
- FETCH 3 body[] — get message 3
- MOVE / COPY — organise messages
## Port Numbers
| Protocol | Port |
|----------|------|
| TELNET | 23 |
| DNS | 53 |
| HTTP | 80 |
| HTTPS | 443 |
| FTP | 21 |
| SMTP | 25 |
| POP3 | 110 |
| IMAP | 143 |