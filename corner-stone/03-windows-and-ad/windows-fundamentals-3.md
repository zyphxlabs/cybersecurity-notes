## Windows Update

Microsoft keeps releasing security updates and patches for Windows and they usually come on the second Tuesday of every month which people call Patch Tuesday but if something is really critical they can push it anytime without waiting for that day. Windows 10 and later you cannot ignore updates you can only postpone them. Command to open it is control /name Microsoft.WindowsUpdate

## Windows Security

This is basically the central place where all your security tools live on Windows and it uses status icons to tell you whats going on

- Green — device is protected no action needed
- Yellow — something to review
- Red — needs immediate attention

## Virus and Threat Protection

This has two parts current threats and protection settings. For scanning you have three options

- Quick Scan — only checks common threat locations
- Full Scan — checks everything takes over an hour
- Custom Scan — you pick which files to scan

Threat history keeps track of quarantined threats which are isolated and blocked from running and allowed threats which are the ones you manually said were fine. Protection settings have real-time protection which stops malware from installing or running and cloud-delivered protection which uses cloud data to give faster protection and controlled folder access which blocks unknown apps from modifying your files and you can also set exclusions for files or folders you want skipped during scanning. Ransomware protection also exists but it needs controlled folder access to be enabled first

## Windows Firewall

Windows Firewall controls what traffic is allowed in and out through ports basically think of it like a security guard checking everything entering or leaving. It has three profiles

- Domain — when you are connected to a domain controller
- Private — home or trusted networks
- Public — public places like coffee shops and airports

Command to open it is WF.msc

## Microsoft Defender SmartScreen

This protects against phishing websites malware sites and malicious file downloads and you can set it to Warn Block or Off. Always keep it on Warn or Block never turn it off completely

## Device Security

soThere is a Core Isolation which  has something called Memory Integrity which basically stops malicious code from injecting itself into high security processes. Then there is TPM which stands for Trusted Platform Module it is a hardware chip that handles cryptographic operations and the good thing is malware cannot touch it because it is tamper resistant. BitLocker encrypts entire drives so if your device gets stolen the data is protected it works best when TPM is installed but it is not available on all Windows editions

## Volume Shadow Copy Service (VSS)

Now coming to the VSS  so it creates snapshots of your data at a point in time and is used for system restore and backup and these are stored in the System Volume Information folder. The security relevance here is that ransomware specifically targets and deletes VSS snapshots which makes recovery impossible without an offline backup so never rely on VSS alone always keep offline backups

## Living Off The Land

This is when attackers use built-in Windows tools to avoid detection so they do not bring their own malware they just use what is already on the system. Examples are PowerShell WMI certutil rundll32. This makes it really hard to detect because these are all legitimate tools just being used maliciously