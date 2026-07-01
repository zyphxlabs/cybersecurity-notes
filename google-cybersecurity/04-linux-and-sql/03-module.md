## Communicating with bash

Talking to the OS through shell is basically like a conversation you type something it responds back with something the dollar sign before cursor is basically telling you its ready for a new command commands and arguments in linux are case sensitive so even file names matter with capital and small letters

An argument is basically extra info a command needs to actually do something like echo alone does nothing but echo "you are doing great" gives it something to actually output some commands can even take multiple arguments at once

## Navigating file system

Think of FHS like a tree everything starts from root and branches out root is always represented with a single slash and every other directory branches off from there this hierarchy helps system know exactly where to find stuff

- Home directory holds personal folders for each user
- Bin holds binary files and executables
- Etc holds configuration files for the system
- Tmp holds temporary files and attackers love using this since anyone can modify data here
- Mnt is used to mount external drives like usb or hard disks

File path is basically the address of a file or folder absolute path always starts from root like /home/analyst/projects while relative path starts from wherever you currently are like using dot for current directory and double dot for going one level up

- pwd shows your current working directory
- ls shows files and folders inside current directory
- cd lets you move between directories

Reading file content also matters a lot for analyst work

- cat shows the whole file content at once
- head shows just first 10 lines by default
- tail shows just last 10 lines by default and is useful for checking latest log entries
- less lets you scroll through file content page by page instead of dumping everything at once

## Filtering info

Filtering basically means picking out data that matches specific condition instead of scanning everything manually this saves so much time when dealing with big files or logs

Grep is used to search a file for specific string like grep OS updates.txt returns every line containing OS from that file this becomes super useful when you're trying to trace something specific like an error or malware signature across huge log files

Piping is when you take output of one command and feed it as input to another command using the pipe symbol so you can chain commands together like ls /home/analyst/reports piped into grep users to filter file names containing users

Find command is used to search files and directories based on specific criteria like name size or when it was last modified

- Using -name searches by exact name and its case sensitive
- Using -iname does same thing but ignores case
- Using -mtime searches based on when file was last modified counted in days
- Asterisk is used as wildcard meaning zero or more unknown characters

## Managing directories and files

Organizing stuff properly in linux makes life way easier when you need to find something quickly especially during incident response

- mkdir creates a new directory
- rmdir deletes an empty directory and warns you if its not empty so you dont accidentally lose files
- touch creates a new empty file
- rm deletes a file and its hard to recover once deleted so be careful
- mv moves a file to new location and also works for renaming files
- cp copies a file to new location while keeping the original intact

Nano is basically a simple text editor built into most linux distros beginners find it easy since its not complicated like vim you open a file with nano filename edit it then save using ctrl o and exit using ctrl x since nano doesnt auto save you gotta remember to save before exiting

You can also redirect output straight into files using the right angle bracket which overwrites the file completely or double right angle bracket which just appends new content at the end without deleting whats already there this is risky if used carelessly since overwriting cant really be undone

## Permissions and ownership

Permissions decide what kind of access someone has over a file or directory this ties directly into authorization which is basically about controlling who gets to touch what data access should always be need to know basis nobody should have more access than they actually need

- Read lets you view file content or see whats inside a directory
- Write lets you modify a file or create new files inside directory
- Execute lets you run a file if its a program or enter into a directory

Every file has three types of owners user which is whoever created the file group which is a bunch of users grouped together and other which is basically everyone else on the system

Permissions show up as a 10 character string like drwxrwxrwx first character tells if its a directory using d or a regular file using hyphen then next three characters are for user next three for group and last three for other each set can have r w x or hyphen if that permission is missing

You use ls -l to see permissions clearly ls -a to see hidden files which start with a dot and ls -la to see both together

## Changing permissions

Chmod is the command used to actually change permissions on a file or directory the whole thing works using letters like u for user g for group and o for other combined with plus to add permission minus to remove permission and equals to set permission exactly as specified overwriting whatever was there before

So something like chmod g+w,o-r access.txt means we are giving write permission to group and taking away read permission from other you separate multiple changes using commas and no spaces after them

This all connects to principle of least privilege basically meaning nobody should get more access than what they actually need for their job like if hr file only needs owner access you'd run chmod g-rw bonuses.txt to strip group permissions since they dont need it

## Authentication and root user

Authentication is basically proving you are who you say you are while authorization decides what youre allowed to access once you're in root user or superuser is the most powerful account on the system that can do literally anything create delete or modify any file

Logging in directly as root is considered bad practice because if attackers get into that account they get full control also its way too easy to accidentally run a wrong command and destroy something permanently plus theres no way to track who actually ran what if everyone logs in as root

This is why sudo exists it temporarily gives elevated permission to a specific user without needing to log into root account directly sudo comes from super user do only users listed in sudoers file are allowed to use it

## User management commands

Useradd is used to add a new user into the system only root or sudo users can run this you can also assign primary group using -g option or add them to extra groups using -G option

Usermod is used to modify an already existing user like changing their group home directory or login name using -a along with -G makes sure old groups arent replaced when adding new supplemental groups

Userdel removes a user completely from system by default it doesnt touch their home directory files unless you add -r option which deletes those too you should always keep backups before doing this since its permanent

Chown is used to change ownership of a file either user or group ownership using a colon before group name specifies its a group change instead of user

## Getting help inside linux

Linux has a massive online community since its open source so most common problems already have answers somewhere online like on unix and linux stack exchange where answers are ranked based on votes so good answers show up first

- Man shows detailed manual info about any command
- Whatis gives quick one line description of what a command does
- Apropos searches man page descriptions for a keyword useful when you dont even know the exact command name yet
- Adding -a with apropos lets you search using two keywords together to narrow down results
