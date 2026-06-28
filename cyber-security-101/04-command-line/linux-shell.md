## What is a Shell

The shell is basically the interface between you and the operating system. A GUI is like ordering food at a restaurant someone else does the work but you have less control and a CLI is like cooking yourself more effort but you control everything and the shell is like the recipe book that makes it all happen. It gives you way more control and efficiency than a GUI ever could

## Checking and Switching Shells

- `echo $SHELL` — see which shell you are currently using
- `cat /etc/shells` — list all shells installed on the system
- just type the shell name like `zsh` to switch temporarily for that session
- `chsh -s /usr/bin/zsh` — change your default shell permanently

## Types of Shells

- Bash — default on most distros has tab completion and command history and is the most widely documented
- Fish — beginner friendly with built-in syntax highlighting and spell correction but limited for scripting
- Zsh — more modern has advanced tab completion and spell correction and can be heavily customised using oh-my-zsh

## Basic Commands

- `pwd` — shows where you currently are in the file system
- `cd foldername` — move into a directory
- `ls` — list all files in the current directory
- `cat file.txt` — read and print the contents of a file
- `grep "word" file.txt` — search for a specific word inside a file

## Shell Scripting

Shell scripting is basically saving a bunch of commands into a `.sh` file so instead of typing them one by one every time you just run the file and it does everything at once. It is mainly used to automate repetitive tasks

### Steps to Run a Script

- `nano myscript.sh` — create the script file
- add `#!/bin/bash` at the very top which is called the shebang and tells the system which shell to use
- `chmod +x myscript.sh` — give the file execute permission
- `./myscript.sh` — run it

### Variables

Variables let you store a value and reuse it anywhere in the script. `read` is used to take input from the user while the script is running

```bash
echo "Enter your name:"
read name
echo "Welcome, $name"
```

### Loops

Loops let you repeat something a set number of times without writing it out over and over

```bash
for i in {1..10};
do
  echo $i
done
```

### Conditionals

Conditionals let the script make decisions based on whether something is true or false

```bash
if [ "$name" = "John" ]; then
  echo "Access granted"
else
  echo "Access denied"
fi
```

### Comments

Use `#` to write comments in a script they are completely ignored when the script runs and are just there so you or someone else reading the code can understand what is going on