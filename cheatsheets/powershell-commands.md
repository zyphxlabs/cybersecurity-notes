# PowerShell Commands Cheatsheet

## Basic

- `Get-Command` — list all cmdlets

- `Get-Help cmdletname` — get help for any cmdlet

- `Get-Alias` — list all aliases



## File System

- `Get-ChildItem` — list files and folders

- `Set-Location -Path "path"` — change directory

- `New-Item -Path "path" -ItemType "File"` — create file

- `New-Item -Path "path" -ItemType "Directory"` — create folder

- `Remove-Item -Path "path"` — delete file or folder

- `Copy-Item -Path "src" -Destination "dest"` — copy

- `Move-Item -Path "src" -Destination "dest"` — move

- `Get-Content -Path "file"` — read file contents



## Filtering

- `Get-ChildItem | Sort-Object Length` — sort by size

- `Get-ChildItem | Where-Object -Property "Extension" -eq ".txt"` — filter

- `Get-ChildItem | Select-Object Name,Length` — select properties

- `Select-String -Path "file" -Pattern "word"` — search in file



## System Info

- `Get-ComputerInfo` — full system info

 -`Get-LocalUser` — list local users

- `Get-NetIPConfiguration` — network config

- `Get-NetIPAddress` — all IP addresses

- `Get-Process` — running processes

- `Get-Service` — all services

- `Get-NetTCPConnection` — active connections

- `Get-FileHash -Path "file"` — file hash

- `Get-Item -Path "file" -Stream \*` — view ADS



## Remote Execution

- `Invoke-Command -ComputerName Server01 -ScriptBlock { command }` — run on remote machine

