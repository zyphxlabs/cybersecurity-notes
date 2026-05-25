# Linux Commands Cheatsheet

## Navigation
- `pwd` — where am I right now
- `ls` — list files
- `ls -la` — list all files including hidden ones
- `ls -a` — show hidden files
- `cd foldername` — enter a folder
- `cd ..` — go back one folder
- `cd /etc` — go to a specific path directly

## File Management
- `touch filename` — create empty file
- `mkdir foldername` — create a folder
- `rm filename` — delete a file
- `rm -R foldername` — delete folder and everything inside
- `cp file1 file2` — copy a file
- `mv file1 file2` — move or rename a file
- `file filename` — identify what type of file it is

## Reading Files
- `cat filename` — print file contents
- `cat os-release` — read Linux distribution info
- `nano filename` — open file in text editor

## System Info
- `whoami` — current logged in user
- `uname -a` — kernel version and system info
- `df -h` — disk space in human readable format
- `ps` — show running processes
- `ps aux` — show all processes from all users
- `top` — real time process monitor

## Searching
- `find -name filename` — find a file by name
- `find -name *.txt` — find all files with extension
- `grep "word" filename` — search inside a file
- `grep -R "word" /etc/` — search recursively through folders
- `wc -l filename` — count lines in a file

## Permissions
- `chmod 777 file` — everyone full access
- `chmod 755 file` — owner full, others read and execute
- `chmod 644 file` — owner read write, others read only
- `su username` — switch to another user
- `su -l username` — switch and land in their home directory

## Services
- `systemctl start servicename` — start a service
- `systemctl stop servicename` — stop a service
- `systemctl enable servicename` — start on boot
- `systemctl status servicename` — check service status

## Processes
- `kill PID` — kill a process by ID
- `command &` — run in background
- `fg` — bring background process to foreground

## Package Management
- `apt install softwarename` — install software
- `apt remove softwarename` — remove software
- `apt update` — update package list

## Important Directories
- `/etc` — system config files
- `/var/log` — log files
- `/root` — root user home directory
- `/tmp` — temporary files, cleared on reboot

## Operators
- `&` — run command in background
- `&&` — run two commands together
- `>` — redirect output to file, overwrites
- `>>` — append output to file