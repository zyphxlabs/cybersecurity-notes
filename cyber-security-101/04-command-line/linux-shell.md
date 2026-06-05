# Linux Shells \& Shell Scripting



## What is a Shell

Interface between you and the OS.

-GUI = ordering food.

-CLI = cooking yourself.

-Shell = the recipe book.

More control and efficiency than GUI.



## Checking and Switching Shells

- `echo $SHELL` — see current shell

- `cat /etc/shells` — list all installed shells

- type shell name e.g. `zsh` to switch temporarily

- `chsh -s /usr/bin/zsh` — change default permanently



## Types of Shells

-Bash — default on most distros, tab completion, command history, widely documented

-Fish — beginner friendly, built-in syntax highlighting, spell correction, limited scripting

-Zsh — modern, advanced tab completion, spell correction, very customisable via oh-my-zsh



## Basic Commands

- `pwd` — where you are

- `cd foldername` — change directory

- `ls` — list files

- `cat file.txt` — read a file

- `grep "word" file.txt` — search inside a file



## Shell Scripting

Set of commands saved in a `.sh` file so you run them all at once.

Used to automate repetitive tasks.



### Steps to run a script:

1. `nano myscript.sh` — create the file

2. Add `#!/bin/bash` at the top (shebang)

3. `chmod +x myscript.sh` — give execute permission

4. `./myscript.sh` — run it


### Variables

Store a value and reuse it. `read` takes user input.

```bash

echo "Enter your name:"

read name

echo "Welcome, $name"

```



\### Loops

```bash

for i in {1..10};

do

&#x20; echo $i

done

```



\### Conditionals

```bash

if \[ "$name" = "John" ]; then

&#x20; echo "Access granted"

else

&#x20; echo "Access denied"

fi

```



\### Comments

Use `#` — ignored when script runs, just for readability

