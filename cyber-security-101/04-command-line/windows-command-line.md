## Why Use CLI Over GUI

Most people go with GUI because it feels easier but once you get used to CLI it is just faster and more efficient overall

- Speed — no clicking around just type and go
- Lower resource usage — works fine on older or limited hardware
- Automation — batch scripts are way easier than trying to automate GUI clicks
- Remote management — you can SSH into servers routers and IoT devices easily

## Basic System Info

- `ver` — show Windows version
- `systeminfo` — show OS RAM and CPU details
- `set` — show environment variables and system Path
- `driverquery` — list all installed drivers
- `help` — general help
- `command /?` — help for any specific command like `ping /?`
- `cls` — clear the screen

If any output is too long just add `| more` at the end then press Space to scroll and CTRL+C to quit

## Network

- `ipconfig` — show IP address subnet mask and default gateway
- `ipconfig /all` — full info including DNS DHCP and MAC address
- `ping example.com` — check if you can reach a host
- `tracert example.com` — shows every hop between you and the target
- `nslookup example.com` — get the IP of a domain
- `nslookup example.com 1.1.1.1` — same but use a specific DNS server
- `netstat` — show active connections
- `netstat -abon` — detailed view with ports programs and PIDs where `-a` shows all connections and listening ports `-b` shows which program owns each port `-o` shows the process ID and `-n` shows numbers instead of hostnames

## Directories

- `cd` — show where you currently are
- `cd foldername` — go into a folder
- `cd ..` — go up one level
- `dir` — list files and folders
- `dir /a` — include hidden files
- `dir /s` — include all subfolders
- `tree` — visual folder structure
- `mkdir name` — create a folder
- `rmdir name` — delete a folder

## Files

- `type file.txt` — print file contents to screen
- `more file.txt` — view file page by page
- `copy a.txt b.txt` — copy a file
- `move file.txt C:\folder` — move a file
- `del file.txt` — delete a file

You can use `*` as a wildcard like `copy *.txt C:\Backup` to apply a command to multiple files at once

## Processes

- `tasklist` — show all running processes
- `tasklist /FI "imagename eq sshd.exe"` — filter by name
- `taskkill /PID 1234` — kill a process by its PID

## Other Commands

- `chkdsk` — check disk for errors
- `sfc /scannow` — scan and repair system files
- `shutdown /s` — shut down
- `shutdown /r` — restart
- `shutdown /a` — cancel a scheduled shutdown