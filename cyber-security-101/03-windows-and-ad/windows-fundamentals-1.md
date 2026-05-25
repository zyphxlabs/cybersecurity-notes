# Windows Fundamentals 1

## Windows History
Windows has been dominant in home and corporate environments since 1985.
Because of this it has always been a major target for hackers and malware.

Version timeline:
- Windows XP — very popular, long running
- Windows Vista — poorly received, quickly phased out
- Windows 7 — widely adopted, now end of life
- Windows 8 — short lived like Vista
- Windows 10 — widely used, end of support October 2025
- Windows 11 — current version, Home and Pro editions
- Windows Server 2025 — current server version

## The Windows Desktop
Main components of the Windows GUI:
- Desktop — shortcuts to programs, folders, files
- Start Menu — access to all apps, files, settings
- Taskbar — shows open applications
- Notification Area — clock, volume, network icons
- Search Box — find files, apps, settings quickly
- Task View — switch between open windows

## File System — NTFS
Modern Windows uses NTFS — New Technology File System.
Before NTFS there was FAT16/FAT32 and HPFS.
FAT is still used on USB drives and MicroSD cards.

NTFS advantages over FAT:
- Supports files larger than 4GB
- Set specific permissions on files and folders
- File and folder compression
- Encryption using EFS

NTFS Permissions:
- Full Control — do everything
- Modify — read, write, delete
- Read and Execute — view and run files
- List Folder Contents — see what is inside
- Read — view only
- Write — create and edit

## Alternate Data Streams (ADS)
ADS is an NTFS feature that lets files contain more than one stream of data.
Windows Explorer does not show ADS by default.
Malware writers use ADS to hide malicious data inside legitimate files.
Can be viewed using PowerShell.

## Important Windows Folders
C:\Windows — the Windows operating system folder
C:\Windows\System32 — critical system files, do not delete anything here
C:\Users — all user profile folders live here
%windir% — environment variable pointing to Windows directory

## User Accounts
Two types of local user accounts:
- Administrator — can make system wide changes, install programs, manage users
- Standard User — can only change their own files, cannot install programs

User profiles are created at C:\Users\username on first login.

## User Account Control (UAC)
UAC was introduced in Windows Vista to protect the system.
Even administrators do not run with full privileges by default.
When a program needs elevated permissions UAC prompts for confirmation.
This reduces the risk of malware making system changes silently.
Shield icon on a program means UAC will prompt before it runs.

## Settings vs Control Panel
Settings — introduced in Windows 8, primary location for system changes now.
Control Panel — older interface, still used for complex settings.
Both accessible from the Start Menu.
Sometimes Settings redirects you to Control Panel for advanced options.

## Task Manager
Shows all running applications and processes.
Also shows CPU and RAM usage under Performance tab.
Access by right clicking the Taskbar.
Click More Details to see full information.