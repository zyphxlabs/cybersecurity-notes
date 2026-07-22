# Operating Systems Basics

## What is an Operating System
Software that manages hardware and lets me run programs.
Without an OS my computer is just hardware with no way to interact with it.
Common ones: Windows, Linux, macOS.

## Windows Basics
Most common desktop OS in the world.
File system starts at C:\
Important locations:
C:\Windows\System32 — core system files
C:\Users\ — user folders
C:\Program Files — installed programs

Registry — stores all Windows settings and configurations.
Task Manager — shows running processes, CPU and RAM usage.
Event Viewer — shows logs of everything that happened on the system.
This is what SOC analysts use to investigate incidents.

## Linux CLI Basics
Linux is used by almost every server and security tool.
Everything in Linux is a file.
CLI means Command Line Interface — I type commands instead of clicking.

Commands I use constantly:
pwd — where am I
ls -la — show all files including hidden
cd — move between folders
cat — read a file
grep — search inside files
chmod — change file permissions
sudo — run as administrator

## Windows CLI Basics
Windows has its own command line too.
ipconfig — show IP address
netstat — show network connections
tasklist — show running processes
dir — list files in a folder
cd — move between folders

## Operating System Security
Principle of Least Privilege — give users only the access they need.
Patch Management — keep OS updated to fix known vulnerabilities.
Antivirus — detects and removes malicious software.
Firewall — controls what traffic enters and leaves the system.
User Account Control — stops programs making changes without permission.