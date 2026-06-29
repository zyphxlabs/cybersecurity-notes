## What is PowerShell

PowerShell is a tool from Microsoft built for task automation and system management and what makes it different from regular command line tools is that it is object oriented meaning it returns actual objects not just plain text which makes it way more powerful. It was built on the .NET framework and works on Windows macOS and Linux. The old tool cmd.exe just could not handle complex enterprise tasks so Jeffrey Snover created PowerShell in 2006 to fix that and then in 2016 PowerShell Core was released as open source and cross platform

## Basic Cmdlets

Cmdlets follow a Verb-Noun naming pattern which makes them really easy to understand just by reading them. The ones you will use most to get started are `Get-Command` which lists all available cmdlets and functions `Get-Help cmdletname` which shows the documentation for any cmdlet you want to learn about and `Get-Alias` which lists all shortcuts like `dir` being an alias for `Get-ChildItem`. For modules you can use `Find-Module -Name "name"` to search online and `Install-Module -Name "name"` to install one

## File System Cmdlets

- `Get-ChildItem` — list files and folders same as ls or dir
- `Set-Location -Path "path"` — change directory same as cd
- `New-Item -Path "path" -ItemType "File"` — create a file
- `New-Item -Path "path" -ItemType "Directory"` — create a folder
- `Remove-Item -Path "path"` — delete a file or folder
- `Copy-Item -Path "source" -Destination "dest"` — copy a file
- `Move-Item -Path "source" -Destination "dest"` — move a file
- `Get-Content -Path "file"` — read file contents same as cat

## Filtering and Piping

The pipe symbol `|` passes the output of one cmdlet into another and because PowerShell pipes actual objects instead of just text like CMD does it is significantly more powerful. So instead of just passing a string you are passing structured data with properties you can filter and sort. Some useful examples are `Get-ChildItem | Sort-Object Length` to sort files by size and `Get-ChildItem | Where-Object -Property "Extension" -eq ".txt"` to filter only txt files and `Get-ChildItem | Select-Object Name,Length` to show only specific properties. For searching inside files `Select-String -Path "file" -Pattern "word"` works like grep. The comparison operators you will use with filtering are

- `-eq` — equal to
- `-ne` — not equal to
- `-gt` — greater than
- `-ge` — greater than or equal to
- `-lt` — less than
- `-le` — less than or equal to
- `-like` — matches a pattern with a wildcard

## System Information Cmdlets

- `Get-ComputerInfo` — full system information
- `Get-LocalUser` — list all local user accounts
- `Get-NetIPConfiguration` — network interfaces IP DNS and gateway
- `Get-NetIPAddress` — all IP addresses on the system
- `Get-Process` — all running processes with CPU and memory usage
- `Get-Service` — status of all services running or stopped
- `Get-NetTCPConnection` — active TCP connections
- `Get-FileHash -Path "file"` — generate a SHA256 hash of a file
- `Get-Item -Path "file" -Stream *` — view Alternate Data Streams on a file

## Remote Execution

PowerShell lets you run commands on remote machines using `Invoke-Command -ComputerName Server01 -ScriptBlock { command }` which is incredibly useful for system admins who need to manage multiple machines at once and also for penetration testers doing enumeration. You can execute scripts and commands across multiple machines in one go which is why this is one of the most powerful features PowerShell has

## Why PowerShell Matters for Security

Both the blue team and red team use PowerShell heavily which is why understanding it is essential for anyone in security. Blue team uses it to automate log analysis detect anomalies and extract IOCs and red team uses it for system enumeration remote command execution and bypassing defences. It sits right at the intersection of both sides