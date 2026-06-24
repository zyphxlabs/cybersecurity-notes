## Text Editors

There are two main text editors you use in the terminal. Nano is the simple one and honestly the one you'll use most when starting out and VIM is the harder one but more powerful and works on basically any terminal.

Nano commands:
- `nano filename` — create or open a file
- CTRL+X — exit
- CTRL+O — save
- CTRL+W — search for text

VIM is harder to learn but once you get it its really good for writing code and its available everywhere so worth learning eventually.

## Processes

Processes are basically everything running on your system and Linux gives you commands to see and control all of them.

- `ps` — show running processes for current user
- `ps aux` — show all processes from all users
- `top` — real time view of running processes
- `kill PID` — kill a process by its ID

There are different kill signals and they don't all do the same thing. SIGTERM kills the process but lets it clean up first which is the nice way. SIGKILL just kills it immediately no cleanup at all. SIGSTOP pauses it.

## Managing Services

Services are things like web servers that need to keep running in the background and systemctl is how you control them.

- `systemctl start apache2` — start a service
- `systemctl stop apache2` — stop a service
- `systemctl enable apache2` — start service on boot automatically
- `systemctl disable apache2` — stop it from starting on boot
- `systemctl status apache2` — check if its running

## Background and Foreground

Sometimes you want a command to keep running without blocking your terminal so you throw it in the background.

- `command &` — run a command in the background
- CTRL+Z — pause and background a running process
- `fg` — bring it back to foreground

## Crontabs

Crontabs are basically how you schedule things to run automatically at specific times without doing it yourself every time. The format is MIN HOUR DOM MON DOW CMD and each field represents a time unit. So something like `0 */12 * * * cp -R /home/user/Documents /var/backups/` backs up your Documents folder every 12 hours automatically. The `*` just means any value for that field.

- `crontab -e` — edit your crontab

## Package Management

apt is how you install and remove software on Linux and GPG keys are what verify the software is actually legit before it installs.

- `apt install softwarename` — install software
- `apt remove softwarename` — remove software
- `apt update` — update package list
- `add-apt-repository` — add a new software source

## Log Files

Log files live in `/var/log` and they basically record everything that happens on the system which makes them really useful when you're trying to investigate something or just monitor what's going on. Apache2 keeps an access log and error log so admins can see every request hitting the web server. fail2ban logs track brute force attempts and UFW logs show firewall activity.