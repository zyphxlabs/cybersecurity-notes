# Windows Fundamentals 2 — System Configuration Tools
---

## Computer Management (compmgmt)
Three main sections: System Tools, Storage, Services and Applications.

### Task Scheduler
- Runs apps or scripts automatically at specified times
- Can trigger at login, logoff, or on a schedule
- View scheduled tasks: Task Scheduler Library
- Create a task: Actions pane → Create Basic Task

### Event Viewer
- Shows events that occurred on the computer — audit trail
- Used to diagnose problems and investigate activity
- Three panes: left (tree), middle (events), right (actions)
- Five event types: Critical, Error, Warning, Information, Verbose
- Standard logs under Windows Logs: Application, Security, Setup, System, Forwarded Events

### Shared Folders
- Shows all shared folders others can connect to
- C$ and ADMIN$ are default Windows shares
- Sessions tab shows currently connected users
- Open Files tab shows what connected users are accessing

### Performance Monitor (perfmon)
- Views performance data in real-time or from log file
- Used for troubleshooting performance issues locally or remotely

### Device Manager
- View and configure hardware attached to the computer
- Can disable hardware from here

### Disk Management
- Set up new drives
- Extend or shrink partitions
- Assign or change drive letters

### Services
- Shows all services and their statuses
- Service startup types:
  - Automatic — starts every time system boots
  - Manual — starts only when triggered
  - Disabled — should not run at all

### WMI Control
- Configures Windows Management Instrumentation service
- Allows scripting languages to manage Windows locally and remotely
- WMIC is deprecated in Windows 10 21H1 — PowerShell replaces it

---

## User Account Control (UAC)
Four security levels:
- **Always notify** — highest security, notifies for everything, desktop dims
- **Notify for apps** — default setting, notifies only when apps make changes
- **Notify without dimming** — same as above but screen does not dim
- **Never notify** — all notifications off, not recommended

---

## System Information (msinfo32)
Gathers and displays comprehensive view of hardware, components, and software.

Three sections:
- **Hardware Resources** — advanced technical info
- **Components** — specific hardware device info (Display, Input etc)
- **Software Environment** — installed software, environment variables, network connections

### Environment Variables
- Store information about OS environment
- Example: WINDIR contains location of Windows installation directory
- View via: Control Panel → System → Advanced system settings → Environment Variables

---

## Resource Monitor (resmon)
Displays per-process and aggregate usage information.

Four sections:
- CPU
- Memory
- Disk
- Network

Used for advanced troubleshooting — identifying deadlocked processes and file locking conflicts.

---

## Command Prompt (cmd)
Useful commands:

| Command | What it does |
|---------|-------------|
| `hostname` | Shows computer name |
| `whoami` | Shows logged in user |
| `ipconfig` | Shows network address settings |
| `ipconfig /?` | Shows help manual for ipconfig |
| `netstat` | Shows protocol stats and TCP/IP connections |
| `net` | Manages network resources |
| `net help user` | Shows help for net user subcommand |
| `cls` | Clears the command prompt screen |

---

## Windows Registry (regedit)
Central hierarchical database storing system configuration.

Stores:
- User profiles
- Installed applications
- Hardware information
- Ports being used
- Folder and icon settings

Access via: `regedit`

Warning — making changes to registry can break normal computer operations.

---

## Key Shortcuts to Remember
- `compmgmt` — Computer Management
- `eventvwr` — Event Viewer
- `perfmon` — Performance Monitor
- `msinfo32` — System Information
- `resmon` — Resource Monitor
- `regedit` — Registry Editor
- `cmd` — Command Prompt
