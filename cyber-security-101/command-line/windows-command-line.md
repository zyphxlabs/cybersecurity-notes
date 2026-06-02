\# Windows Command Line



\## Why Use CLI Over GUI



Most people prefer GUI because it's intuitive. But CLI is faster and more efficient once you get used to it.



Advantages:

\- \*\*Speed\*\* — no clicking, just type and go

\- \*\*Lower resource usage\*\* — works on older or limited hardware

\- \*\*Automation\*\* — batch scripts are easier than automating GUI clicks

\- \*\*Remote management\*\* — SSH into servers, routers, IoT devices easily



\---



\## Basic System Info



`ver` — show Windows version



`systeminfo` — show OS, RAM, CPU details



`set` — show environment variables and system Path



`driverquery` — list installed drivers



> If output is too long add `| more` at the end. Press \*\*Space\*\* to scroll, \*\*CTRL+C\*\* to quit.



`help` — general help



`command /?` — help for any specific command e.g. `ping /?`



`cls` — clear the screen



\---



\## Network



`ipconfig` — show IP address, subnet mask, default gateway



`ipconfig /all` — full info including DNS, DHCP and MAC address



`ping example.com` — check if you can reach a host



`tracert example.com` — show every hop between you and the target



`nslookup example.com` — get the IP of a domain



`nslookup example.com 1.1.1.1` — same but use a specific DNS server



`netstat` — show active connections



`netstat -abon` — detailed view with ports, programs and PIDs

\- `-a` all connections and listening ports

\- `-b` which program owns each port

\- `-o` show process ID

\- `-n` show numbers instead of hostnames



\---



\## Directories



`cd` — show where you are



`cd foldername` — go into a folder



`cd ..` — go up one level



`dir` — list files and folders



`dir /a` — include hidden files



`dir /s` — include all subfolders



`tree` — visual folder structure



`mkdir name` — create a folder



`rmdir name` — delete a folder



\---



\## Files



`type file.txt` — print file to screen



`more file.txt` — view file page by page



`copy a.txt b.txt` — copy a file



`move file.txt C:\\folder` — move a file



`del file.txt` — delete a file



> Use `\*` as wildcard — e.g. `copy \*.txt C:\\Backup`



\---



\## Processes



`tasklist` — show all running processes



`tasklist /FI "imagename eq sshd.exe"` — filter by name



`taskkill /PID 1234` — kill a process by PID



\---



\## Other Commands



`chkdsk` — check disk for errors



`sfc /scannow` — scan and repair system files



`shutdown /s` — shut down



`shutdown /r` — restart



`shutdown /a` — cancel a scheduled shutdown

