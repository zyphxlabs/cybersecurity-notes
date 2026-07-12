## Automation In Security

Automation is basically using tech to cut down manual work for stuff thats repetitive and boring. As a security analyst you cant just sit and watch every single login attempt so thats where automation comes in and python is really good for this kind of work

There was this example about a healthcare company that stores patient records and they wanted a timeout policy so if someone takes more than three minutes to login it locks them out cause that could mean someone is guessing password

Another example was a law firm where attackers were breaking into employee accounts and stealing client info so the analyst had to track login timestamp ip address and location and flag accounts based on stuff like

- login happening in early morning hours
- login coming from a location outside the two established work zones
- same user logged in from two different ip addresses at once

Last example was an org that wanted to flag any user with more than three failed logins in the last 30 minutes by parsing a static txt log file with username ip address timestamp and login status then using conditionals to flag them

## Opening And Reading Files

To work with logs in python you first gotta open the file and python gives a clean way to do that using with keyword. With handles errors and manages external resources so it automatically closes the file once your done with it instead of you doing it manually

The syntax looks like this with open("logs.txt", "r") as file: and breaking it down

- with starts the block and takes care of closing file automatically
- open() is the function that actually opens the file first parameter is filename or path second parameter tells python what you wanna do with it
- "r" means read "w" means write and overwrite "a" means append without deleting existing stuff
- as assigns whatever open() gives back to a variable name like file

If the file is in the same directory as your python file you just need the filename but if its somewhere else you need the absolute file path which starts from the root directory

Once file is open you use .read() method which turns the whole file into one big string like file_text = file.read() and this string can now be stored in a variable and used like any other string with stuff like .index() or len()

## Writing To Files

Writing works kinda similar you open file with "w" if you wanna replace everything thats already there or make a brand new file, and "a" if you just wanna add new stuff at the end without touching whats already there

Once opened in write or append mode you use .write() method to actually put string data into the file like file.write("jrafael") and if you dont use with keyword properly and forget to close file manually sometimes the data doesnt fully write so better to just stick with with

## Parsing With Split And Join

Parsing means turning data into something more readable so you can actually work with it easier. Once you read a file into one long string you use .split() to break it into a list

Split works by separating the string wherever it finds the character you pass in as argument, so "elarson,bmoreno,tshah".split(",") becomes a list of three separate usernames. If you dont pass anything in it just splits on whitespace which includes spaces and newlines both

So for something like a log file where each username is on its own line you can just do updates = updates.split() without any argument and it breaks it up by the newlines automatically

Join does the opposite thing it takes a list and turns it back into one string. The syntax is a bit different though instead of list.join() you gotta do "separator".join(list) so like ",".join(["elarson","bmoreno","tshah"]) gives you back "elarson,bmoreno,tshah". You can also use "\n" as the separator to put each element on its own new line

This matters cause if you wanna use .write() on a file you need a string not a list so you gotta join it back first before writing

## Building A Login Check Algorithm

This was the big example where we combined everything to build something that checks if a user has three or more failed login attempts. The log file had one username per line representing a failed attempt

The strategy was first import file and split it into a list called usernames then loop through the list counting how many times a specific username shows up

We build a function called login_check() that takes two parameters login_list for the list of failed attempts and current_user for whoever is trying to log in right now. Inside the function

- start a counter variable at 0
- loop through login_list with a for loop using i as loop variable
- inside loop use an if statement to check if i equals current_user and if true add 1 to counter
- after the loop use if-else to check if counter is 3 or more, if yes print account locked message else let them log in

Ran it on eraab who had two entries in first eight names and it correctly said account locked which means logic is working fine

## Debugging Basics

Debugging is just the process of finding and fixing errors in your code and honestly this can take just as much time as writing the code itself. There are three main types of errors

- syntax errors which is when you mess up the actual python language like forgetting a colon after function header or missing quotation mark, these are usually easy since python tells you exactly which line
- logic errors which dont give you any error message at all the code runs fine but gives wrong result like using less than instead of less than or equal to in a condition
- exceptions which is when the syntax is totally fine but python still cant run it for example dividing by zero or trying to access an index that doesnt exist

For syntax errors the message usually tells you exactly where the problem is like SyntaxError or IndentationError which is actually a subclass of SyntaxError. For exceptions you get stuff like NameError when a variable was never assigned, IndexError when you reference an index that doesnt exist in the list, TypeError when you use wrong data type like adding string to integer, and FileNotFound when the file you tried to open just isnt there

## Debugging Strategies

For logic errors and exceptions since they dont always give clear direction you gotta use other strategies

One way is inserting print statements at different points in the code describing where you are like print("line 20") or print("line 55 inside conditional") this helps you see which parts are actually running as expected and which ones arent

Another way is using a debugger which lets you set breakpoints so you can run code in small chunks instead of all at once and check variable values as they change through the program, this is super useful for catching logic errors where a value changed somewhere it shouldnt have

There was also a coworker debugging example where a function had a syntax error from missing colon then a NameError from a misspelled variable application_name that only had one p is left, and after fixing both there was still a logic error where a status code of 200 should print no parsing needed message but didnt. Turned out the return statement was placed before the if statement checking for 200 so function was exiting early before even checking the condition, moving the if statement above the return fixed it completely

Gemini Code Assist was also mentioned as a free ai tool that integrates into ides like vs code and jetbrains and it helps analyze code find errors and suggest fixes but the point was to always double check ai output before trusting it fully since its still evolving tech