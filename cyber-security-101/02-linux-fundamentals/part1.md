# Linux Fundamentals Part 1

## Why Linux
Linux runs almost everything around us.
Websites, ATMs, traffic lights, car systems — all Linux.
It is lightweight, open source and free.
Different versions are called distributions — Ubuntu, Debian, Kali.

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

- `find -name passwords.txt` — find a specific file by name
- `find -name *.txt` — find all files with .txt extension
- `grep "word" filename` — search for a word inside a file
- `grep "81.143.211.90" access.log` — find specific IP in a log file
- `grep -R "PRETTY_NAME" /etc/` — search recursively through all files in a folder
- `wc -l filename` — count number of lines in a file

## Linux Operators

- `&` — run a command in the background
- `&&` — run two commands together, second only runs if first succeeds
- `>` — redirect output to a file, overwrites existing content
- `>>` — append output to a file, does not overwrite

## Examples
- `echo hey > welcome` — creates file called welcome with text hey
- `echo hello >> welcome` — adds hello to the bottom of welcome file
- `command1 && command2` — runs both commands in one line