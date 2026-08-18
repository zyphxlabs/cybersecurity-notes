## REMnux

REMnux is basically a Linux environment built for analysing suspicious files malware memory and network activity. Think of it like a ready made malware analysis lab where tools like oledump.py Volatility YARA Wireshark and INetSim are already available

The main purpose of REMnux is to give analysts a controlled environment where they can inspect suspicious files and understand what they are doing without having to build everything from scratch. Different tools are used for different parts of the investigation so we can look at documents memory network behaviour and other artefacts

## Oledump.py

Oledump.py is basically a tool that lets us inspect OLE2 files and look at the different streams stored inside them. This becomes really useful with Microsoft Office files because they can contain VBA macros and those macros can be used to execute malicious commands

When we run oledump.py against an Excel file it shows the streams inside the document and marks interesting ones with letters. A capital M means the stream contains a VBA Macro so that is something we would want to investigate further

The `-s` option lets us select a specific stream. For example `oledump.py file.xlsm -s 4` means we are telling oledump to show the fourth stream instead of looking at everything

Sometimes the VBA output is compressed and difficult to read so we can use `--vbadecompress` to decompress the macro and make the actual VBA code easier to understand

A suspicious macro might contain something like PowerShell which is a big clue because Office documents normally should not need to download and execute random programs from external servers

One thing malware authors also do is obfuscate commands by inserting random characters between the real characters. For example a command might have `*` and `^` scattered throughout it and then the VBA code removes those characters before executing the command

This means the command might look useless at first but once we remove the extra characters we can see what it actually does

## Malicious VBA and PowerShell

A VBA macro can be used as an initial execution mechanism where opening a malicious Office document causes the macro to execute commands on the system

One suspicious behaviour is when the macro starts PowerShell and uses options like `-WindowStyle hidden` because this can hide the PowerShell window from the user

Another suspicious option is `-executionpolicy bypass` because it tells PowerShell to bypass its normal execution policy for that execution. By itself this does not automatically mean malware but together with other suspicious behaviour it becomes much more interesting

`Invoke-WebRequest` can be used to communicate with a web server and download something from it. The `-Uri` value tells PowerShell where the resource is located and `-OutFile` tells it where to save the downloaded content

`Start-Process` can then be used to execute the downloaded file

So if we see a chain like Macro → PowerShell → download file → execute file then we should immediately think about a possible malicious payload delivery chain

From a SOC perspective the useful indicators here would include the PowerShell command line the external IP address or domain the downloaded filename the parent process and the final process that gets executed

## INetSim

INetSim is basically a fake internet environment used to simulate common network services during malware analysis. Instead of allowing suspicious software to communicate with the real internet we can give it a controlled environment and observe what it tries to do

This is useful because malware often tries to contact a command and control server download another payload or make DNS requests. We want to see this behaviour without giving the malware unrestricted access to the real internet

INetSim can simulate services such as DNS HTTP HTTPS FTP SMTP and POP3 which means a suspicious program can make network requests and still receive responses from our controlled environment

The `dns_default_ip` setting controls the IP address returned in DNS responses. By pointing this to the analysis machine we can make domain lookups resolve back to our simulated environment instead of sending the malware somewhere on the real internet

After starting INetSim the important thing is that the simulation is actually running and the services are listening for connections

A common malware behaviour is downloading a second payload after the initial file executes. We can observe this kind of behaviour in a simulated environment and then inspect the connection logs to see what the malware attempted to access

The connection report is useful because it records information such as the time of the request the protocol the HTTP method the requested URL and the file that was returned

From a SOC perspective this is similar to looking at network telemetry and asking what destination did the process contact what protocol did it use what resource did it request and what happened after the connection

## Volatility

Volatility is basically a memory forensics framework used to investigate RAM captures. Memory can contain information that may no longer exist on disk so analysing it can reveal useful evidence about what was happening on a system

The important thing about memory analysis is that we can investigate running processes command lines loaded DLLs files and potentially injected code instead of only looking at files stored on the disk

Volatility works using plugins and each plugin focuses on a different type of evidence

- `windows.pstree.PsTree` shows processes in a parent child relationship
- `windows.pslist.PsList` shows processes found in memory
- `windows.cmdline.CmdLine` shows process command line arguments
- `windows.filescan.FileScan` searches memory for file objects
- `windows.dlllist.DllList` shows DLLs and other loaded modules
- `windows.psscan.PsScan` scans memory for process structures
- `windows.malfind.Malfind` looks for memory regions that may contain injected code

PsTree is useful because process relationships can reveal suspicious execution chains. For example if an Office application starts PowerShell and PowerShell starts an unknown executable then the parent child relationship itself becomes useful evidence

PsList gives us a view of processes that were running while the memory was captured. CmdLine gives us more context because a process name alone might look normal but its command line could reveal suspicious arguments or commands

FileScan can find file objects that were present in memory while DllList shows modules loaded into processes. These can help us understand what programs were doing at the time of the capture

PsScan is useful because it searches memory for processes using another method and can sometimes reveal processes that are not visible through a normal process listing

Malfind is especially interesting when looking for process injection because it searches for memory regions that have characteristics commonly associated with injected or suspicious code

## Volatility Preprocessing

When analysing a memory image we might need to run many Volatility plugins and save their results separately. Doing this manually every time would be slow so we can use a shell loop to automate the process

The basic idea is to put the plugin names inside a variable and then run Volatility once for every value in that variable

The `-q` option means quiet mode so unnecessary progress information is not printed and `-f` tells Volatility which memory image we want to analyse

The `>` operator redirects the output into a file instead of printing it directly to the terminal

This is called preprocessing because we are preparing the evidence before the actual investigation. Once the results are saved we can search through the text files much faster and go back to the original memory image only when we need deeper analysis

## Strings

The `strings` command is a simple Linux utility that searches a file for readable character sequences. It can be surprisingly useful during malware and memory analysis because memory often contains useful text such as URLs IP addresses usernames file paths commands and error messages

The normal `strings` command looks for ASCII text while the `-e` option allows us to look for different character encodings

- `strings file` extracts ASCII strings
- `strings -e l file` extracts 16 bit little endian strings
- `strings -e b file` extracts 16 bit big endian strings

Using multiple formats is useful because Windows commonly uses Unicode and not everything will appear correctly when we only search for normal ASCII strings

The output can also be redirected into files so we can search through the results later instead of repeatedly processing the entire memory image

## Malware Analysis Flow

The overall idea is basically to take a suspicious artefact and look at it from different angles

If we have a suspicious Office document we can use oledump.py to inspect its internal streams and check for VBA macros. If we find a macro we can decompress it and look for suspicious commands such as PowerShell downloads or execution

If the malware communicates with external infrastructure we can use a simulated network such as INetSim to observe the network behaviour without allowing the sample to freely communicate with the real internet

If we have a memory capture we can use Volatility to investigate processes command lines DLLs files and possible process injection. We can then use strings to extract readable information that may help us find additional indicators

The important part is that no single tool gives us the complete picture. One tool shows us what the file contains another shows us what the malware tries to do over the network and another shows us what was happening inside memory

This is basically how malware analysis starts coming together. We collect different pieces of evidence and connect them to understand the complete behaviour of the suspicious program