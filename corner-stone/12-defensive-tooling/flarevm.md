## FlareVM Overview
Flarevm stands for forensics logic analysis and reverse engineering, its basically a huge curated toolkit built specifically for reverse engineers malware analysts incident responders forensic investigators and pentesters. It was put together by the flare team at fireeye and its meant to help unravel how malware behaves and dig into the details hiding inside executables

## Tool Categories
Reverse engineering is basically like solving a puzzle backward, you take a finished product apart to figure out how it actually works. Debugging on the other hand is about finding errors understanding why they happen and fixing the code so they dont happen again. Tools in this space include ghidra which is an nsa developed open source reverse engineering suite, x64dbg which is an open source debugger for both x64 and x32 binaries, ollydbg for reversing at the assembly level, radare2 which is a more advanced open source reversing platform, binary ninja for disassembling and decompiling, and peid which detects packers cryptors and compilers

Disassemblers and decompilers help analysts understand a piece of malwares behaviour logic and control flow by breaking it down into something more readable. Cff explorer is a pe editor for analyzing and editing portable executable files, hopper disassembler works as a debugger disassembler and decompiler all in one, and retdec is an open source decompiler for machine code

Static and dynamic analysis are two different approaches to examining malware, static means looking at the code without running it while dynamic means actually observing its behaviour while it runs. Process hacker is a sophisticated memory editor and process watcher, peview lets you view pe files for analysis, dependency walker shows an executables dll dependencies, and die which stands for detect it easy identifies packers compilers and cryptors

Forensics and incident response is about collecting analyzing and preserving digital evidence while also handling detection containment eradication and recovery from attacks. Volatility is a ram dump analysis framework for memory forensics, rekall is another memory forensics framework, and ftk imager handles disk image acquisition and analysis

Network analysis covers studying networks to spot patterns optimize performance and understand traffic behaviour. Wireshark is the go to network protocol analyzer for recording and examining traffic, nmap does vulnerability detection and network mapping, and netcat lets you read and write data across network connections

File analysis is about examining files for security threats and checking file permissions. Fileinsight lets you look through and edit binary files, hex fiend is a light and fast hex editor, and hxd is another hex editor for viewing and editing binary files

Scripting and automation is all about using scripts to automate repetitive tasks and cut down on human error. Python tools here are mostly automation focused, and powershell empire is a framework built for powershell post exploitation

Sysinternals suite is a set of advanced utilities for managing troubleshooting and diagnosing windows systems. Autoruns shows what executables are set to run at boot, process explorer gives detailed info on running processes, and process monitor logs real time process and thread activity

## Core Investigation Tools
Procmon or process monitor is a powerful windows tool that records issues with system apps in real time, tracking file system registry and thread process activity. Its especially useful for malware research troubleshooting and forensic investigations. If youre filtering for a process like lsass.exe and see it reading files related to authentication thats usually normal, but since lsass is a common target for credential dumping attacks like mimikatz you'd want to keep an eye out for weird access patterns around it

Process explorer gives deep insight into whats running on a system, showing the full list of processes along with their linked user accounts. It's really useful for figuring out which program is accessing a specific file or folder, and its great for tracking parent child relationships like when a word document or lnk file spawns another process, which is a common technique threat actors abuse

Hxd is a fast flexible hex editor for editing files memory and drives. It shows hex data on one side and its ascii interpretation on the other, so if a files hex starts with 4d 5a that tells you right away its an executable. It also has a data inspector that lets you view individual bytes across different data types which makes evaluating raw data a lot easier

Cff explorer gives comprehensive file info and lets you generate file hashes for integrity verification, useful for confirming the authenticity of system files or spotting unusual alterations, which matters a lot when malicious code gets hidden inside modified system files

Wireshark is the tool for hunting down suspicious connections examining protocols and spotting possible attacks or data exfiltration. Seeing tlsv1.2 in captured traffic means the connection is encrypted which can either be legitimate traffic or a way for malicious activity to hide itself

Pestudio handles static analysis meaning you study an executables properties without ever running it, which keeps you safe from accidentally executing something malicious. It gives you a ton of info like entropy values, where a higher entropy score suggests the file might be packed or encrypted which is common in malware. It also shows things like architecture compiler used and imported api calls, which help you figure out what the file is actually capable of doing

Floss which stands for flare obfuscated string solver automatically extracts and deobfuscates strings from malware samples using advanced static analysis. Its similar to a basic strings tool but way more powerful since it can pull out both static and dynamically decoded strings, which is useful since malware often hides things like c2 urls ip addresses or api calls behind obfuscation to avoid detection

## Practical Analysis Approach
When investigating a suspicious executable the usual first step is static analysis to gather initial info before running anything. Checking hashes like md5 and sha1 against known malware databases helps determine if the sample is already known or if its something fresh. Metadata can also be revealing, like a file claiming to be a legit windows tool but actually containing text in a language that doesnt match the organizations context, or being located somewhere a legitimate system file would never be found, both are red flags worth digging into

Looking at imported api calls, sometimes called the import address table, tells you a lot about what a file might do once it runs. Functions related to shell execution suggest the malware might spawn other processes, while functions tied to cryptographic operations like aes encryption suggest it might be encrypting data or communications, which could point toward ransomware behaviour or encrypted c2 traffic

For checking network connectivity of a suspicious binary process explorer can show you the parent child relationship and let you dig into its tcp ip properties to see what its connecting to. Its good practice to double check that finding with a second tool like procmon, filtering by the process name to confirm the exact same destination shows up, since relying on just one tool for a conclusion isnt the best practice in analysis work