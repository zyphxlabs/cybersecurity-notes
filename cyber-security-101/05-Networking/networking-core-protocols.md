## DNS
Dns is basically the thing that translates domain names into ip addresses so our browser can actually find the website we typed. It works on udp port 53 and falls back to tcp port 53 when needed. There are different types of records that store different info

- A record — domain to ipv4
- AAAA record — domain to ipv6
- CNAME record — domain to another domain
- MX record — mail server for a domain

We can use `nslookup example.com` to look up the ip of any domain

## WHOIS
Whois is like a giant database that keeps record of every domain that has ever been registered. It shows stuff like registrant name email phone address and dates of registration. We can run `whois example.com` to pull up this info on any domain. If someone doesnt want their real info exposed they can use privacy protection which replaces their real details with proxy details instead

## HTTP
Http is literally how our browser talks to the web server behind the scenes. It runs on tcp port 80 for http and tcp port 443 for the secure version https. There are a few methods that define what action is being done

- GET — fetch a page or file
- POST — send data to server
- PUT — create or overwrite resource
- DELETE — remove resource

## FTP
Ftp was made specifically for transferring files and it runs on tcp port 21. RETR is used to download a file and STOR is used to upload one. Some servers even allow anonymous login which means you dont even need real credentials to get in

## SMTP
Smtp is the protocol that actually sends email from client to server and it runs on tcp port 25. The session starts with HELO then MAIL FROM tells who is sending it then RCPT TO tells who is receiving it then DATA is where you actually write the email body. To end the email you just put a single dot alone on its own line

## POP3
Pop3 downloads the email straight to your device and then deletes it off the server which means its really only meant for single device use. It runs on tcp port 110

- STAT — message count and size
- LIST — list all messages
- RETR 3 — get message 3
- DELE 3 — delete message 3

## IMAP
Imap is different because it syncs your email across multiple devices and keeps everything on the server instead of deleting it. It runs on tcp port 143. We use SELECT inbox to open a mailbox and FETCH 3 body[] to get message 3 and MOVE or COPY to organise messages around

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