## Computer Management

Computer management is basically one place where Windows puts all the important system tools together and it has three main sections which are System Tools Storage and Services and Applications.

Task Scheduler is the one that runs apps or scripts automatically so you don't have to do it yourself. You can set it to trigger at login logoff or just on a schedule and you can view all scheduled tasks in the Task Scheduler Library or create new ones from the Actions pane.

Event Viewer is really useful for investigations because it keeps an audit trail of everything that happened on the computer. It has three panes and five event types which are Critical Error Warning Information and Verbose. Under Windows Logs you get Application Security Setup System and Forwarded Events.

Shared Folders shows everything others can connect to on your machine. Windows has default shares called C$ and ADMIN$ already and you can see who is currently connected under Sessions and what they are accessing under Open Files.

Performance Monitor lets you view performance data in real time or from a log file which is useful when something is running slow and you need to figure out why. Device Manager is where you view and configure hardware and you can even disable things from there. Disk Management handles drives so setting up new ones extending or shrinking partitions and changing drive letters all happens here.

Services shows everything running in the background and each one has a startup type:

- Automatic — starts every time system boots
- Manual — starts only when triggered
- Disabled — should not run at all

WMI Control configures the Windows Management Instrumentation service which lets scripting languages manage Windows locally and remotely. Worth knowing that WMIC is deprecated in Windows 10 21H1 and PowerShell replaces it now.

## User Account Control

UAC basically controls how much Windows bothers you when something tries to make changes and it has four levels:

- Always notify — highest security notifies for everything and desktop dims
- Notify for apps — default setting only notifies when apps make changes
- Notify without dimming — same as above but screen does not dim
- Never notify — all notifications off not recommended

## System Information

msinfo32 gathers and displays everything about your hardware components and software in one place. It has three sections which are Hardware Resources for advanced technical info Components for specific hardware like Display and Input and Software Environment which covers installed software environment variables and network connections.

Environment variables are basically stored information about the OS environment so for example WINDIR contains the location of the Windows installation directory. You can view them through Control Panel then System then Advanced system settings then Environment Variables.

## Resource Monitor

Resource Monitor shows exactly what each process is using and in total across four sections which are CPU Memory Disk and Network. It is used for advanced troubleshooting like finding deadlocked processes and file locking conflicts.

## Command Prompt

Some useful commands to know:

- `hostname` — shows computer name
- `whoami` — shows logged in user
- `ipconfig` — shows network address settings
- `ipconfig /?` — shows help manual for ipconfig
- `netstat` — shows protocol stats and TCP/IP connections
- `net` — manages network resources
- `net help user` — shows help for net user subcommand
- `cls` — clears the screen

## Windows Registry

Registry is a central database where Windows stores basically everything about the system in a hierarchical structure. It keeps user profiles installed applications hardware information ports being used and folder and icon settings. You access it through regedit but making changes here can genuinely break things so you have to be careful.

## Key Shortcuts

- `compmgmt` — Computer Management
- `eventvwr` — Event Viewer
- `perfmon` — Performance Monitor
- `msinfo32` — System Information
- `resmon` — Resource Monitor
- `regedit` — Registry Editor
- `cmd` — Command Prompt