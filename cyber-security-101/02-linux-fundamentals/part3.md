# Linux Fundamentals Part 3

## Text Editors

### Nano
Simple terminal text editor. Easy to use.
- `nano filename` — create or open a file in nano
- CTRL+X — exit
- CTRL+O — save
- CTRL+W — search for text

### VIM
Advanced text editor. Harder to learn but more powerful.
Works on all terminals. Good for writing code.

## Processes

- `ps` — show running processes for current user
- `ps aux` — show all processes from all users
- `top` — real time view of running processes
- `kill PID` — kill a process by its ID

Kill signals:
- SIGTERM — kill process but let it clean up first
- SIGKILL — kill process immediately no cleanup
- SIGSTOP — pause a process

## Managing Services

- `systemctl start apache2` — start a service
- `systemctl stop apache2` — stop a service
- `systemctl enable apache2` — start service on boot
- `systemctl disable apache2` — stop service starting on boot
- `systemctl status apache2` — check if service is running

## Background and Foreground

- `command &` — run a command in the background
- CTRL+Z — pause and background a running process
- `fg` — bring a background process back to foreground

## Crontabs
Crontabs schedule commands to run automatically at set times.

Format: MIN HOUR DOM MON DOW CMD

Example — backup Documents every 12 hours:
0 */12 * * * cp -R /home/user/Documents /var/backups/

- `crontab -e` — edit your crontab
- * means any value for that field

## Package Management

- `apt install softwarename` — install software
- `apt remove softwarename` — remove software
- `apt update` — update package list
- `add-apt-repository` — add a new software repository
- GPG keys verify the integrity of software before installing

## Log Files
Log files are stored in `/var/log`
Important logs:
- Apache2 web server logs — access log and error log
- fail2ban logs — monitors brute force attempts
- UFW logs — firewall activity

Logs help monitor system health and investigate attacks.
Admins check access logs to see every request made to a web server.