# Windows CMD Cheatsheet

**System Info**

* `ver` — show Windows version
* `systeminfo` — show OS, RAM, CPU details
* `set` — show environment variables and system Path
* `driverquery` — list installed drivers

**Navigation**

* `cd` — where am I right now
* `cd foldername` — go into a folder
* `cd ..` — go back one folder
* `dir` — list files and folders
* `dir /a` — include hidden files
* `dir /s` — include all subfolders
* `tree` — visual folder structure

**File Management**

* `mkdir foldername` — create a folder
* `rmdir foldername` — delete a folder
* `copy a.txt b.txt` — copy a file
* `move file.txt C:\folder` — move a file
* `del file.txt` — delete a file
* `erase file.txt` — same as del
* `copy *.txt C:\Backup` — wildcard copy

**Reading Files**

* `type file.txt` — print file to screen
* `more file.txt` — view page by page

**Network**

* `ipconfig` — show IP, subnet mask, gateway
* `ipconfig /all` — full info including DNS, DHCP, MAC
* `ping example.com` — check if you can reach a host
* `tracert example.com` — show every hop to the target
* `nslookup example.com` — get IP of a domain
* `nslookup example.com 1.1.1.1` — use a specific DNS server
* `netstat` — show active connections
* `netstat -abon` — show ports, programs and PIDs

**Processes**

* `tasklist` — show all running processes
* `tasklist /FI "imagename eq sshd.exe"` — filter by name
* `taskkill /PID 1234` — kill a process by PID

**Other**

* `cls` — clear the screen
* `help` — general help
* `command /?` — help for any command
* `chkdsk` — check disk for errors
* `sfc /scannow` — scan and repair system files
* `shutdown /s` — shut down
* `shutdown /r` — restart
* `shutdown /a` — cancel scheduled shutdown

**Operators**

* `|` — pipe output to another command
* `| more` — paginate long output
* `>` — redirect output to file
* `>>` — append output to file
* `&&` — run two commands together

