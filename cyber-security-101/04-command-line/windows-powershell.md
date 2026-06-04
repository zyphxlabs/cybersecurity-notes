# Windows PowerShell

## What is PowerShell
PowerShell is a tool from Microsoft for task automation and system management.
It is object oriented — returns objects not just plain text.
Works on Windows, macOS and Linux.
Built on the .NET framework.

## Why PowerShell Was Created
Old tools like cmd.exe could not handle complex enterprise tasks.
Jeffrey Snover created PowerShell in 2006 to fix this.
In 2016 PowerShell Core was released as open source and cross platform.

## Basic Cmdlets
Cmdlets follow Verb-Noun naming — easy to understand what they do.

- `Get-Command` — lists all available cmdlets and functions
- `Get-Help cmdletname` — shows documentation for any cmdlet
- `Get-Alias` — lists all aliases like dir for Get-ChildItem
- `Find-Module -Name "name"` — search online for modules
- `Install-Module -Name "name"` — install a module from online

## File System Cmdlets
- `Get-ChildItem` — list files and folders, same as ls or dir
- `Set-Location -Path "path"` — change directory, same as cd
- `New-Item -Path "path" -ItemType "File"` — create a file
- `New-Item -Path "path" -ItemType "Directory"` — create a folder
- `Remove-Item -Path "path"` — delete file or folder
- `Copy-Item -Path "source" -Destination "dest"` — copy a file
- `Move-Item -Path "source" -Destination "dest"` — move a file
- `Get-Content -Path "file"` — read file contents, same as cat

## Filtering and Piping
Pipe symbol | passes output of one cmdlet to another.
PowerShell pipes objects not just text — more powerful than CMD.

- `Get-ChildItem | Sort-Object Length` — sort files by size
- `Get-ChildItem | Where-Object -Property "Extension" -eq ".txt"` — filter by extension
- `Get-ChildItem | Select-Object Name,Length` — show only specific properties
- `Select-String -Path "file" -Pattern "word"` — search inside files like grep

Comparison operators:
- `-eq` — equal to
- `-ne` — not equal to
- `-gt` — greater than
- `-ge` — greater than or equal to
- `-lt` — less than
- `-le` — less than or equal to
- `-like` — matches a pattern with wildcard

## System Information Cmdlets
- `Get-ComputerInfo` — full system information
- `Get-LocalUser` — list all local user accounts
- `Get-NetIPConfiguration` — network interfaces, IP, DNS, gateway
- `Get-NetIPAddress` — all IP addresses on the system
- `Get-Process` — all running processes with CPU and memory usage
- `Get-Service` — status of all services running or stopped
- `Get-NetTCPConnection` — active TCP connections
- `Get-FileHash -Path "file"` — generate SHA256 hash of a file
- `Get-Item -Path "file" -Stream *` — view Alternate Data Streams on a file

## Remote Execution
- `Invoke-Command -ComputerName Server01 -ScriptBlock { command }` — run command on remote machine
- Powerful for system admins and penetration testers
- Can execute scripts and commands on multiple machines at once

## Why PowerShell Matters for Security
Blue team — automate log analysis, detect anomalies, extract IOCs
Red team — system enumeration, remote command execution, bypass defences
Both sides use PowerShell heavily — understanding it is essential
