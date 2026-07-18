## TLS

Tls basically adds confidentiality integrity and authenticity to protocols that already exist so like http becomes https smtp becomes smtps pop3 becomes pop3s and imap becomes imaps it doesnt replace the protocol it just wraps security around it

Ssl came first in 1995 then tls replaced it in 1999 and now tls 1.3 is the current version people still say ssl out of habit but its actually tls running behind the scenes

For a server to use tls it needs a tls certificate and that certificate has to be signed by a certificate authority ca if you make your own self signed certificate it cant prove authenticity because no third party actually confirmed it so browsers dont fully trust it

When you connect to an https site the steps go tcp handshake first then tls handshake then finally the actual http data starts flowing so theres extra steps before any real data moves

If tls is not being used all the traffic can be seen in plain text in wireshark like literally anyone sniffing the network can just read whats being sent

## Secure Port Numbers

- http insecure 80 secure 443
- smtp insecure 25 secure 465 or 587
- pop3 insecure 110 secure 995
- imap insecure 143 secure 993

## SSH

Ssh basically came to replace telnet because telnet sent everything in cleartext and ssh encrypts all the traffic instead so nobody can read it in between

It listens on tcp port 22 and you connect using ssh username@hostname if you want graphical interface support you add -X at the end like ssh hostname -X

It supports password auth public key auth and even two factor auth so theres multiple ways to prove who you are

Ssh protects confidentiality and integrity and also prevents man in the middle attacks and you can even tunnel other protocols through it so it kinda works like a mini vpn

## SFTP

Sftp is basically secure file transfer but it runs over ssh so it uses the same port 22 you connect with sftp username@hostname and then use get filename to download and put filename to upload people mix this up with ftps a lot but its not the same thing

## FTPS

Ftps is just normal ftp but secured with tls and it runs on port 990 it needs a tls certificate to actually work and honestly its harder to configure than sftp because it uses separate control and data connections so more stuff can go wrong

## VPN

A vpn basically connects devices or even whole branches over the internet as if they were sitting on the same private network the vpn client encrypts your traffic and sends it through a tunnel to the vpn server

So when you visit a website it only sees the vpn server ip not your real one thats why people use it to bypass geo restrictions or get around isp censorship your isp only sees encrypted traffic and has no idea what your actually doing

Some vpns leak your real ip without you knowing so you gotta run a dns leak test to check if its actually hiding you properly also vpn is illegal in some countries so always check local laws before using one