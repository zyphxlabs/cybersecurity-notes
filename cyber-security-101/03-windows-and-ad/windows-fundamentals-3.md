# Windows Fundamentals 3

## Windows Update
Microsoft releases security updates and patches for Windows.
Updates usually come on the second Tuesday of every month — called Patch Tuesday.
Critical updates can be pushed anytime without waiting for Patch Tuesday.
Windows 10 and later — updates cannot be ignored, only postponed.
Command to open Windows Update: control /name Microsoft.WindowsUpdate

## Windows Security
Central place to manage all security tools on Windows.
Status icons:
- Green — device is protected, no action needed
- Yellow — safety recommendation to review
- Red — something needs immediate attention

## Virus and Threat Protection
Two parts — Current Threats and Protection Settings.

Scan types:
- Quick Scan — checks common threat locations only
- Full Scan — checks everything, takes over an hour
- Custom Scan — you choose which files to scan

Threat history:
- Quarantined threats — isolated and prevented from running
- Allowed threats — threats you manually allowed to run

Protection settings:
- Real-time protection — stops malware from installing or running
- Cloud-delivered protection — faster protection using cloud data
- Controlled folder access — blocks unknown apps from modifying files
- Exclusions — files or folders skipped during scanning
- Ransomware protection — requires controlled folder access enabled

## Windows Firewall
Controls what traffic is allowed in and out through ports.
Think of it as a security guard checking everything entering or leaving.

Three firewall profiles:
- Domain — used when connected to a domain controller
- Private — home or trusted private networks
- Public — public networks like coffee shops and airports

Command to open firewall: WF.msc

## Microsoft Defender SmartScreen
Protects against phishing websites, malware sites, and malicious file downloads.
Settings: Warn, Block, or Off.
Always leave it on Warn or Block.

## Device Security
Core Isolation:
- Memory Integrity — stops malicious code from injecting into high security processes

TPM — Trusted Platform Module:
- Hardware chip that handles cryptographic operations
- Tamper resistant — malware cannot touch its security functions

BitLocker:
- Encrypts entire drives to protect data if device is stolen
- Works best with TPM installed
- Not available on all Windows editions

## Volume Shadow Copy Service (VSS)
Creates snapshots of data at a point in time.
Used for system restore and backup.
Stored in System Volume Information folder.

Security relevance:
Ransomware specifically targets and deletes VSS snapshots.
This makes recovery impossible without an offline backup.
Always keep offline backups — never rely on VSS alone.

## Living Off The Land
Attackers use built-in Windows tools to avoid detection.
They do not bring their own malware — they use what is already there.
Examples: PowerShell, WMI, certutil, rundll32.
This makes detection harder because legitimate tools are being used maliciously.