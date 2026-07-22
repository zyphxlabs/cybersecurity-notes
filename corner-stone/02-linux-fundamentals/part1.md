## Why Linux

Linux is honestly everywhere and most people don't even realize it. Websites ATMs traffic lights car systems all running on Linux. It's lightweight open source and free which is probably why it took over everything. Different versions exist and they are called distributions like Ubuntu Debian Kali.

## Basic Commands

- `echo` — prints text to the terminal
- `whoami` — shows current logged in user
- `ls` — lists files and folders in current directory
- `ls Pictures` — lists contents of a folder without entering it
- `cd foldername` — move into a folder
- `cd ..` — go back one folder
- `cat filename` — read contents of a file
- `pwd` — shows full path of where you are right now

## Finding Files

Finding files in Linux is actually really useful once you get it like instead of clicking around you just tell it exactly what to look for and it finds it. grep is especially useful when you're going through logs trying to find something specific like an IP address.

- `find -name passwords.txt` — find a specific file by name
- `find -name *.txt` — find all files with .txt extension
- `grep "word" filename` — search for a word inside a file
- `grep "81.143.211.90" access.log` — find specific IP in a log file
- `grep -R "PRETTY_NAME" /etc/` — search recursively through all files in a folder
- `wc -l filename` — count number of lines in a file

## Linux Operators

Operators are basically shortcuts that let you do more with one line like chaining commands or redirecting where the output goes instead of it just printing to the terminal.

- `&` — run a command in the background
- `&&` — run two commands together second only runs if first succeeds
- `>` — redirect output to a file overwrites existing content
- `>>` — append output to a file does not overwrite

So for example `echo hey > welcome` creates a file called welcome with the text hey inside it and `echo hello >> welcome` just adds hello to the bottom without touching what was already there. The `&&` one is useful when you want two things to run in one go but only if the first one actually worked.