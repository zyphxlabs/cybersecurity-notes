## Windows History

Windows has been around since 1985 and it basically took over home and corporate environments which also made it the biggest target for hackers and malware out there. Every version had its own story like Vista and Windows 8 both flopped pretty quickly but XP and 7 people actually loved them. Windows 10 ends support October 2025 and Windows 11 is the current one with Home and Pro editions. For servers the current version is Windows Server 2025.

- Windows XP — very popular long running
- Windows Vista — poorly received quickly phased out
- Windows 7 — widely adopted now end of life
- Windows 8 — short lived like Vista
- Windows 10 — widely used end of support October 2025
- Windows 11 — current version Home and Pro editions
- Windows Server 2025 — current server version

## The Windows Desktop

The desktop is basically just the GUI with everything you need to interact with the system and it has a few main parts:

- Desktop — shortcuts to programs folders files
- Start Menu — access to all apps files settings
- Taskbar — shows open applications
- Notification Area — clock volume network icons
- Search Box — find files apps settings quickly
- Task View — switch between open windows

## File System NTFS

Modern Windows runs on NTFS which stands for New Technology File System. Before this there was FAT16 FAT32 and HPFS. FAT is still used on USB drives and MicroSD cards but NTFS is way more capable especially for actual system use.

NTFS advantages over FAT:
- Supports files larger than 4GB
- Set specific permissions on files and folders
- File and folder compression
- Encryption using EFS

NTFS also has its own permission system which is really important from a security perspective:

- Full Control — do everything
- Modify — read write delete
- Read and Execute — view and run files
- List Folder Contents — see what is inside
- Read — view only
- Write — create and edit

## Alternate Data Streams

ADS is an NTFS feature that lets a file hold more than one stream of data which sounds harmless but malware writers use this to hide malicious data inside legitimate files. Windows Explorer doesn't even show ADS by default so most people have no idea it's there. You can view it using PowerShell.

## Important Windows Folders

- C:\Windows — the main Windows operating system folder
- C:\Windows\System32 — critical system files don't delete anything here
- C:\Users — all user profile folders live here
- %windir% — environment variable that points to the Windows directory

## User Accounts

There are two types of local user accounts in Windows. Administrator can make system wide changes install programs and manage other users. Standard User can only change their own files and cannot install programs. User profiles get created at C:\Users\username the first time someone logs in.

## User Account Control

UAC was introduced in Windows Vista basically to stop malware from making system changes silently. Even if you're an administrator you don't run with full privileges by default and when something needs elevated permissions UAC just pops up and asks you to confirm. If you see a shield icon on a program that means UAC will prompt before it actually runs.

## Settings vs Control Panel

Settings came in with Windows 8 and is now the main place for system changes. Control Panel is the older one but still used for more complex stuff. Both are accessible from the Start Menu and sometimes Settings will actually redirect you to Control Panel for advanced options.

## Task Manager

Task Manager shows all running applications and processes and also shows CPU and RAM usage under the Performance tab. You access it by right clicking the Taskbar and if you click More Details you get the full information view.