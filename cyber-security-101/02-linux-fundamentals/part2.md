## SSH

SSH stands for Secure Shell and it basically lets you remotely connect to and control another Linux machine and everything sent over it is encrypted so nobody can just intercept what you're doing.

- `ssh username@MACHINE_IP` — connect to a remote machine

## Flags and Switches

Commands have a default behaviour but flags let you extend what they can do like `ls` by default just shows files but `ls -a` shows hidden ones too. If you ever forget what flags exist just run `--help` or open the man page.

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

Every file has three permission sets for owner group and others and each one gets rwx which stands for read write execute. The way the numbers work is r equals 4 w equals 2 and x equals 1 and you just add them up for each group so 777 means everyone has full access and 644 means owner can read and write but everyone else can only read.

- `rwxrwxrwx` = 777 — everyone has full access
- `rwxr-xr-x` = 755 — owner full others read and execute
- `rw-r--r--` = 644 — owner read and write others read only
- `rwx------` = 700 — only owner has access
- `chmod 755 filename` — set permissions using numbers
- `su username` — switch to another user
- `su -l username` — switch and land in that user's home directory

## Important Linux Directories

These directories are important to know especially when doing pentesting because useful stuff lives in specific places.

- `/etc` — system config files sudoers passwd and shadow files live here
- `/var` — variable data and log files live in /var/log
- `/root` — home directory for the root user
- `/tmp` — temporary files cleared on reboot and any user can write here which makes it useful in pentesting as a place to store scripts after getting access