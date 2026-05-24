# Linux Fundamentals Part 2

## SSH
SSH stands for Secure Shell.
It lets you remotely connect to and control another Linux machine.
All data sent over SSH is encrypted.

- `ssh username@MACHINE_IP` — connect to a remote machine

## Flags and Switches
Commands have default behaviour but flags extend what they can do.

- `ls -a` — show hidden files and folders
- `ls --help` — show all available options for a command
- `man ls` — open the full manual for ls
- `man commandname` — works for any command

## File and Folder Management

- `touch filename` — create a new empty file
- `mkdir foldername` — create a new folder
- `rm filename` — delete a file
- `rm -R foldername` — delete a folder and everything inside
- `cp file1 file2` — copy a file
- `mv file1 file2` — move or rename a file
- `file filename` — tells you what type of file it is

## File Permissions
Every file has three permission sets — owner, group, others.
r = read = 4
w = write = 2
x = execute = 1

Add them up for each group:
- `rwxrwxrwx` = 777 — everyone has full access
- `rwxr-xr-x` = 755 — owner full, others read and execute
- `rw-r--r--` = 644 — owner read and write, others read only
- `rwx------` = 700 — only owner has access

- `chmod 755 filename` — set permissions using numbers
- `su username` — switch to another user
- `su -l username` — switch and land in that user's home directory

## Important Linux Directories

- `/etc` — system config files. sudoers, passwd and shadow files live here.
- `/var` — variable data. Log files live in /var/log
- `/root` — home directory for the root user
- `/tmp` — temporary files. Cleared on reboot. Any user can write here.
  Useful in pentesting — good place to store scripts after getting access.