## CAPA Basics
When analyzing potentially malicious software theres always a risk of compromising your own machine unless you got a proper sandbox or isolated environment to test in. There are two main types of analysis, dynamic and static, this one is all about static analysis using a tool called capa

Capa stands for common analysis platform for artifacts, it was made by the fireeye mandiant team. It looks at executable files like pe files elf binaries dotnet modules shellcode and even sandbox reports and figures out what capabilities they have by matching the file against a big set of rules describing common behaviours. So instead of manually reverse engineering a binary from scratch capa basically automates years of reverse engineering knowledge into rules, which makes it way more accessible even if youre not an expert at reversing. This makes it super useful for malware analysis and threat hunting since understanding what a binary can actually do is a big part of incident response

## Running CAPA
Running it is pretty straightforward, you just point capa at the binary you want to analyze and it loads its rule set then starts analyzing. It can take a good while especially on bigger files. There are two useful flags worth knowing

- -v or --verbose — gives a more detailed result document
- -vv or --vverbose — gives an even more detailed result, takes longer to process too

The basic output gives you a table with hashes like md5 sha1 sha256, the analysis type which is usually static, the target os, file format like pe, and the architecture like i386

## MITRE ATT&CK Mapping
Capa maps its findings to the mitre attack framework which is basically a giant knowledge base documenting the tactics and techniques threat actors use at every stage of an attack, from getting initial access all the way to lateral movement and everything in between

The output format usually looks like tactic::technique::identifier, so something like defense evasion::obfuscated files or information::t1027 breaks down as defense evasion being the tactic obfuscated files or information being the technique and t1027 being the identifier. Sometimes theres also a sub technique involved which just adds another layer like t1027.005 for indicator removal from tools specifically. This mapping helps analysts connect a files behaviour directly to the attackers playbook which narrows down the scope of an investigation a lot

## MAEC
Maec stands for malware attribute enumeration and characterization, its basically a standardized language for describing malware behaviours artefacts and how different malware samples relate to each other. Capa mainly tags files with two common maec values

- Launcher — file shows behaviour similar to malware like dropping payloads activating persistence connecting to c2 servers or running specific functions
- Downloader — file shows behaviour like fetching more payloads from the internet pulling updates running secondary stages or grabbing config files

## Malware Behavior Catalogue (MBC)
Mbc is designed to support malware analysis stuff like labelling similarity analysis and standardized reporting, basically its a catalogue of malware objectives and behaviours. It can link back to attack techniques but doesnt duplicate that info, it just complements it

The format is usually objective::behavior::method[identifier] or a shorter objective::behavior::[identifier] when theres no specific method involved

Objective is based on attack tactics but tailored specifically for malware characterization, mbc also adds two extra ones not in attack

- Anti-behavioral analysis — malware tries to avoid detection by messing with tools like sandboxes or debuggers
- Anti-static analysis — malware tries to make static analysis harder so its intentions are tougher to figure out

Besides those there's also stuff like collection command and control credential access defense evasion discovery execution exfiltration impact lateral movement persistence and privilege escalation, all pretty similar in spirit to their attack counterparts but framed around malware behaviour specifically

Micro-objective is a step below objective and covers lower level actions that arent necessarily malicious by themselves but often get abused, stuff like

- Process — creating processes setting thread context terminating processes checking mutex
- Memory — allocating memory changing memory protection freeing memory
- Communication — network traffic over dns ftp http icmp smtp
- Data — checking strings compressing encoding and decoding data

Behavior and micro behavior together make up what gets shown in the behavior column of the final output, and methods are basically sub techniques tied to a specific behavior, like base64 or xor being methods under the encode data behavior

## Capability and Namespace
Capa groups its findings using namespaces so similar rules sit together. The format is basically capability(rule name)::top level namespace/namespace, so something like reference anti-vm strings would fall under the top level namespace anti-analysis and the namespace anti-vm/vm-detection

Some of the top level namespaces include

- Anti-analysis — rules that detect malware trying to evade analysis through obfuscation packing or anti-debugging
- Collection — rules around gathering data for exfiltration
- Communication — rules for network behaviour like c2 traffic or data transmission
- Compiler — rules that identify the build environment or compiler used
- Data-manipulation — rules around altering data like encryption or encoding
- Executable — rules about attributes of the executable file itself like pe sections
- Host-interaction — rules about interacting with the host system like reading writing or modifying files
- Impact — rules about the potential consequences of the malwares behaviour
- Linking — rules about dynamically loading external code or libraries
- Load-code — rules about dynamically loading or executing code at runtime
- Persistence — rules about maintaining access to a compromised system
- Nursery — basically a staging area for rules that arent fully polished yet, so sometimes a capability you'd expect to be under one namespace ends up here instead

Each capability shown in the output is literally the name of the rule thats matched, and the rule file itself just has dashes between the words instead of spaces, so a capability like reference base64 string comes straight from a rule file called reference-base64-string.yml

## Verbose Output and Deeper Analysis
Running with -vv gives a way more detailed breakdown showing exactly why a rule was triggered and what conditions matched, but this output can get massive real quick, thousands of lines long, which makes it hard to go through in a plain text editor or terminal

To make this easier you can combine -j with -vv and redirect the output into a json file, something like capa -j -vv target.bin > output.json. This json can then get loaded into capa explorer which is a web based viewer, way easier to browse through than raw text. You can search and filter through capabilities and click into any one of them to see the actual rule content and which specific strings or conditions triggered it

For example if a rule references vmware detection, capa explorer would show you the actual regex pattern like string: /VMWare/i being matched inside the file, meaning capa found that literal string reference which points to vm detection behaviour. Same goes for something like scheduled task detection, where the rule might be looking for strings like schtasks and create together, and if both show up capa flags it as a persistence mechanism through scheduled tasks

This kind of deep dive into the actual matched conditions is what makes capa useful beyond just a surface level report, you get to see the exact reasoning behind every capability it flags instead of just taking its word for it