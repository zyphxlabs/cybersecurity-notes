## Linux history

Linux came from two separate efforts in early 1990s one was Linus Torvalds who wanted to improve UNIX and make it open source he built the Linux kernel which was the big breakthrough part around same time Richard Stallman was working on GNU which was also UNIX based but it was missing a kernel so basically Torvalds kernel plus Stallman GNU work together became what we call Linux today

Linux is open source and licensed under GNU Public License so anyone can use share and modify it freely this open nature built a huge community of developers who keep improving it together thats also why there are over 600 distributions of Linux out there

## Where Linux is used in security

As an analyst you use Linux for checking logs like error logs to see whats going on in a system you also use it for checking access and authorization in identity and access management some distributions are made specifically for certain jobs like digital forensics or pen testing depending on what you need to do

## Linux architecture

Think of it like a flow starting from user going to applications then shell then FHS then kernel then hardware

- User is just the person interacting with the computer and linux allows multiple users to use same resources at same time
- Applications are programs that do specific tasks like nano which is a simple text editor
- Shell is basically the CLI it takes your commands and passes them to the kernel and gives back the response
- FHS is like a filing cabinet it organizes where all the data is stored so system knows where to find it
- Kernel manages processes and memory and talks to hardware using drivers to get tasks done faster
- Hardware is the physical stuff like CPU mouse keyboard

## Distributions explained

Distributions are just different versions of linux built on top of the same kernel like how one engine can be put into different vehicles like trucks cars buses each vehicle serves different purpose same way each distro is built for different need

Because kernel is open source anyone can take it and build their own distro thats why some distros are considered parent ones like Red Hat being parent of CentOS and Slackware being parent of SUSE both Ubuntu and Kali Linux come from Debian

## Kali Linux

Kali Linux is debian derived and made specifically for pen testing and digital forensics it comes preinstalled with a ton of tools you should always run it on a virtual machine so if something goes wrong you can just revert back to previous state without messing up your real system

- Metasploit used to look for and exploit vulnerabilities
- Burp Suite used to test weaknesses in web apps
- John the Ripper used to guess passwords
- Tcpdump used to capture network traffic through command line
- Wireshark used to analyze live and captured traffic with a GUI
- Autopsy used to analyze hard drives and smartphones

## Other distributions

Ubuntu is debian derived too and its known for being user friendly it has both CLI and GUI and comes with a lot of default apps plus you can get more through package manager its also popular for cloud computing so as companies move to cloud you'll deal with ubuntu more

Parrot is also debian based and made for security like kali it has preinstalled pentesting and forensic tools and its considered user friendly because of its GUI

Red Hat Enterprise Linux is different because its subscription based and made for enterprise use unlike the free ones it comes with dedicated support team you can call if something breaks

AlmaLinux exists because CentOS stopped getting stable releases after CentOS 8 in December 2021 so alma was made as a drop in replacement so whatever worked on centos still works fine on alma

## Package managers

A package is basically a piece of software that combines with other packages to form a full application these packages also carry dependencies which are extra files needed to actually run the app package managers help install manage and remove these without headache

Debian based distros like kali ubuntu and parrot use dpkg while red hat based ones like centos use RPM each has their own file extension like .deb for debian ones and .rpm for red hat ones

Theres also tools that make this easier like APT for debian based systems and YUM for red hat based ones these let you install search and manage packages straight from command line without dealing with the raw package manager directly

## Shell

Shell is basically the command line interpreter it takes what you type and passes it to kernel then brings back the result to you think of it as the translator between you and the system since you dont speak binary the shell handles that translation for you

There are many types of shells like bash csh ksh tcsh and zsh but bash is the default and most used one in cybersecurity work throughout this course we mainly deal with bash

## Communicating with shell

There are basically three ways shell responds to you input output or error input is what you type in like echo hello output is what you get back like just hello printed and error happens when system cant understand your command like if you misspell echo as eco it throws an error back at you

This whole input output error cycle is basically how every interaction with shell works nothing more nothing less
