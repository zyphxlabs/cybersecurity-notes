## What is Gobuster
Gobuster is an open source offensive tool written in golang, it enumerates web directories dns subdomains vhosts amazon s3 buckets and google cloud storage through brute force using wordlists and analyzing the responses it gets back. Security folks use it a lot for pentesting bug bounty and general security assessments. In terms of the ethical hacking phases it basically sits between recon and scanning

Enumeration is just listing out all available resources whether theyre accessible or not, like gobuster listing every web directory it finds. Brute force is trying every possibility until something matches, kinda like having ten keys and trying each one on a lock till one works, gobuster uses wordlists to do exactly this

## Gobuster Overview
Its included by default on kali. Running gobuster --help shows the main usage and available commands like completion dir dns fuzz gcs help s3 tftp version and vhost, this room mainly focuses on dir dns and vhost

Some commonly used flags across gobuster in general

- -t / --threads — number of concurrent threads to use, default is 10 but can be bumped up for speed depending on system resources
- -w / --wordlist — path to the wordlist being used, each entry gets appended to the target url
- --delay — time to wait between requests, useful to avoid detection since some servers flag high request rates as enumeration
- --debug — helps troubleshoot when a command throws unexpected errors
- -o / --output — writes results to a file instead of just stdout

Basic example of enumerating a web directory

```
gobuster dir -u "http://www.example.thm/" -w /usr/share/wordlists/dirb/small.txt -t 64
```

gobuster dir sets directory and file enumeration mode, -u sets the target url, -w points to the wordlist small.txt to brute force directories with, and -t 64 bumps threads up to 64 for way better performance

## Dir Mode
Dir mode enumerates website directories and their files, useful during a pentest to map out the structure of a site and what files it holds. A lot of sites follow common conventions in their directory structure which is exactly what makes them brute forceable, like a typical wordpress install having a structure with wp-admin wp-content and wp-includes under html/wordpress

Gobuster is powerful here because it returns status codes for each request which instantly tells you whether you as an outsider can actually access that directory or not

Useful flags for dir mode

- -c / --cookies — passes a cookie along with each request like a session id
- -x / --extensions — specifies which file extensions to scan for like .php or .js
- -H / --headers — configures a full header to send with each request
- -k / --no-tls-validation — skips certificate checking for https, useful for ctf rooms using self signed certs that would otherwise error out
- -n / --no-status — hides status codes from the output to keep things cleaner
- -P / --password and -U / --username — used together for authenticated requests when you already have credentials
- -s / --status-codes — only show responses with specific status codes like 200 or a range like 300-400
- -b / --status-codes-blacklist — hide specific status codes instead, this overrides -s if both are set
- -r / --followredirect — follow redirect responses like 301 or 302 to the new url

Basic command format

```
gobuster dir -u "http://www.example.thm" -w /path/to/wordlist
```

-u and -w are both required for dir mode to actually work. A more practical example

```
gobuster dir -u "http://www.example.thm" -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -r
```

The url is the base path gobuster starts from, so this example is scanning from the root web directory which on a typical apache linux install would be /var/www/html, if you wanted to scan a specific folder like resources youd just set the url to http://www.example.thm/resources instead. The url always needs the protocol included otherwise the scan fails outright. You can use either the ip or the hostname for the host part, but using the ip risks hitting a different site than intended since one ip can host multiple sites through virtual hosting, hostname is safer if youre trying to be precise. Gobuster also doesnt scan recursively, so if it finds a directory you care about youll need to run it again specifically against that path. The -r flag here makes it follow any 301 redirects it receives

Second example using -x to also look for specific file types

```
gobuster dir -u "http://www.example.thm" -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x .php,.js
```

This does the same directory listing as before but also specifically looks for files ending in .php or .js while its at it

## Vhost Mode
Vhost mode brute forces virtual hosts, which are different websites running on the same machine. These can look like subdomains but theyre actually different, vhosts are ip based and live on the same server while subdomains are set up through dns. The core difference in how gobuster scans comes down to this, vhost mode builds a url by combining the hostname from -u with a wordlist entry and navigates to it, while dns mode does an actual dns lookup on the fqdn built from the domain (-d) plus a wordlist entry

Useful flags for vhost mode

- -u / --url — the base target domain for brute forcing vhostnames
- --append-domain — appends the base domain onto each wordlist word, like turning word into word.example.com
- -m / --method — sets which http method to use for requests like get or post
- --domain — appends a domain to each wordlist entry to build a proper hostname when its not already included in the url
- --exclude-length — filters out results based on response body length, handy for cutting out false positives
- -r / --follow-redirect — follows redirects, useful when subdomains happen to redirect somewhere else

Basic command format

```
gobuster vhost -u "http://example.thm" -w /path/to/wordlist
```

-u and -w are required here too. A real example used in the room

```
gobuster vhost -u "http://MACHINE_IP" --domain example.thm -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt --append-domain --exclude-length 250-320
```

This one is a lot more involved than the basic syntax because the test environment doesnt have a fully set up dns infrastructure, which is why --domain and --append-domain both had to be added manually. Looking at the actual request gobuster sends helps explain why, a request like Host www.example.thm breaks down into three parts, www being the subdomain that gobuster fills in from the wordlist, .example being the second level domain, and .thm being the top level domain, both of those last two get set together through the --domain flag

Breaking the command down, gobuster vhost sets vhost enumeration mode, -u sets the url to browse to the machine ip, -w points to the subdomains wordlist and each entry gets appended to whatever domain is configured, if no domain is set explicitly gobuster tries to pull it from the url instead. --domain example.thm sets the actual hostname portion of requests to example.thm. --append-domain is what actually appends that domain onto every wordlist entry, without this flag the hostname being tested would just be raw words like www or blog with nothing after them which breaks the whole scan and causes false positives. --exclude-length filters based on response size to cut down false positives, since without it youll get a flood of fake hits that all tend to share a similar response size, a true positive is generally expected to come back as a clean 200 OK though there can be exceptions to that

## Lab Setup Notes
This room used an ubuntu 20.04 vm as the web server hosting multiple subdomains and vhosts, along with two cms installs, wordpress and joomla. Attackbox already has gobuster installed, running it on your own machine instead just needs the thm vpn connected and gobuster installed manually from its github repo

Since the lab environment relies on a local dns server running on the web server itself, resolving the domains used in the room required editing /etc/resolv-dnsmasq on the attackbox

- open a terminal and run sudo nano /etc/resolv-dnsmasq
- add nameserver MACHINE_IP as the very first line
- save with ctrl+o then enter, exit with ctrl+x
- restart dnsmasq with /etc/init.d/dnsmasq restart

## Summary
Gobuster covers three main modes worth knowing well, dns for enumerating subdomains, dir for enumerating directories and files, and vhost for enumerating virtual hosts. Each mode has its own required and optional flags to fine tune results. The key distinction to remember is that dns mode does actual dns lookups against a configured domain and wordlist, while vhost mode just sends regular web requests using the configured url and wordlist instead