## What is an operating system

An operating system is basically the bridge between the hardware and the user computers only understand binary which is just 0s and 1s so the OS translates our requests into something the hardware can actually do without it we would be stuck typing in binary ourselves

In the 1950s computers could only run one program at a time so people had to wait for a program to finish then reset and load the next one this was super slow and inefficient now because of how OS evolved we can run multiple apps at once and connect external devices like printers and keyboards without even thinking about it

## Common operating systems

- Windows released in 1985 closed source
- macOS released in 1984 partially open source kernel is open but some parts closed
- Linux released in 1991 fully open source anyone can access and edit the code this is why security industry loves it
- ChromeOS launched in 2011 partially open source built from Chromium OS mostly used in education
- Android launched in 2008 open source mobile OS
- iOS launched in 2007 partially open source mobile OS

## Legacy operating systems

A legacy OS is basically an old system that people still use even though its outdated companies keep using them because their old software or equipment isnt compatible with newer systems this happens a lot with embedded software inside machines the problem is these legacy systems stop getting security updates so they become an easy target for new threats security analysts have to stay aware of this because a lot of orgs still run legacy stuff without realizing how exposed they are

## Booting process

When you press the power button you activate a microchip called BIOS or on newer computers after 2007 its UEFI both do the same job which is loading instructions and checking the hardware is healthy the last thing it does is call the bootloader which is the program that actually loads up the operating system once thats done your computer is ready to use as an analyst its good to know that BIOS usually isnt scanned by antivirus so it can be a weak spot for malware to hide

## How a task gets completed

Its basically a four step flow user to application to OS to hardware you as the user open an app to do something like use a calculator the app sends your request to the OS the OS interprets it and passes it to the right hardware component like the CPU for a calculation once the hardware finishes it sends the result back through the OS to the app so you can see it this is useful to know as an analyst because when investigating an incident you can trace back through this flow to figure out where something went wrong

## Resource management

The OS also acts like a conductor of an orchestra making sure every program gets the memory storage and CPU power it needs without wasting anything some tasks need more energy like running an antivirus scan and some need less like opening a calculator all this allocating and de allocating of resources happens behind the scenes and you can actually see it a bit through task manager which shows CPU and memory usage for each task as an analyst this matters because if a system is running slow it could mean resources are being eaten up by malware so checking resource usage can help catch that

## Virtual machines

A virtual machine is basically a fake version of a real computer made entirely out of software it has its own virtual CPU virtual storage and everything a real computer would have you can run multiple VMs on one physical machine by just splitting up the resources like RAM across them each VM runs its own OS like a normal computer would

VMs are useful for security because they create an isolated sandbox so if one VM gets infected with malware it doesnt spread to the host or other VMs security folks even use this on purpose to study malware safely but its not 100 percent safe because malware can sometimes escape the VM and reach the host so you should never fully trust a virtualized system

Hypervisors are what manage all these VMs and share out the physical resources KVM is one to know its open source and built right into the Linux kernel so you dont need extra software to make VMs on Linux

## GUI vs CLI

GUI uses icons and graphics to interact with the computer CLI is just text based commands GUI can only do one task at a time while CLI can handle multiple tasks together which makes it way more powerful once you know how to use it

- GUI is easier for beginners since you just click around
- CLI is faster once you know the commands
- CLI keeps a history file of everything you typed which is huge for security analysts because you can trace back exactly what commands were run
- GUI doesnt really save your actions anywhere by default

This history file thing is really important like if youre following a playbook during an incident you can go back and check your CLI history to confirm you ran everything right or if an attacker got into the system you might be able to trace what they did through that history
