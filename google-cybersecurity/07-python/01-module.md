## How Programming Works

Programming is basically writing a specific set of instructions so a computer can execute tasks and this happens everywhere from computers to phones to pretty much every electronic device we use. There are multiple languages to do this and Python is one of them. What actually happens under the hood is these languages get converted into binary numbers which is just 0s and 1s and that is what the CPU actually understands and executes. Doing this manually would take forever for a human which is why languages like Python exist so we can write less and still tell the computer to do complex stuff.

## Using Python

Python is a general purpose language so it is not just built for one thing it can build websites do data analysis and automate tasks. Before the computer can actually run Python code it needs to go through an interpreter which translates the code into runnable instructions line by line. Also worth remembering there are multiple versions of Python and in this course we are using Python 3 the syntax can differ between versions so keeping track of version matters. Syntax btw just means the rules of how the language should be structured.

## Python In Cybersecurity

In security Python is mainly used for automation and automation just means using tech to cut down manual repetitive effort. Some areas where Python gets used in cybersecurity are

- log analysis
- malware analysis
- access control list management
- intrusion detection
- compliance checks
- network scanning

## Writing And Running Code

When writing in python what we write is called a script or a program these are basically the same thing with subtle difference. Its good practice to always start with a comment which is just a note using the hash symbol explaining what your code intends to do this does not get executed it is just for humans reading it. Then we use print which outputs whatever we put inside the parentheses to the screen if it is a string it needs to go inside quotation marks like print("Hello Python!") once the syntax is correct we run it and it displays.

## Environments To Run Python

Python can run in a few different places

- notebooks which is an online interface for writing storing and running code this is what we use in this course
- integrated development environments aka IDEs which are software with a GUI that give editing help and error correction
- command line where you can access files and directories on your hard drive and run python files directly from there

Notebooks specifically have two kinds of cells code cells where we actually write and run code and markdown cells where we describe the code using markdown language which just formats plain text like headers. Jupyter Notebook and Google Colab are two common notebook environments.

## Data Types

A data type is just a category for the kind of data we are dealing with kind of like how in a kitchen we separate vegetables from meat because it changes how we handle them. Python has string float integer boolean and list as the main ones we focus on here plus tuple dictionary and set as additional ones.

String is basically an ordered sequence of characters like letters numbers symbols and spaces and it always has to be inside quotation marks even if it has numbers in it those numbers cant be used for calculation since its just text. An empty string is just "" with nothing inside.

Integer is a number without a decimal point so stuff like 0 -9 5000 these dont need quotation marks around them.

Float is a number that has a decimal point like 2.1 or even 10.0 counts as float because of the decimal.

Boolean can only be True or False nothing else this is useful for logic later on like when we compare 10 less than 5 that gives False and 9 less than 12 gives True.

List is a collection of data in sequential form placed inside square brackets and separated by commas the elements inside can be any data type even other lists. An empty list is just [].

- tuple is like a list but you cant change whats inside it once set placed in parentheses instead of brackets useful in security when you want something like software identifiers that shouldnt be altered
- dictionary stores key value pairs separated by a colon placed inside curly brackets good for when you want predictable lookup like mapping a number to a building name
- set is an unordered collection of unique values so no duplicates allowed also placed in curly brackets

Also worth noting dividing two numbers with / always gives a float result but if you use // instead it rounds down to the nearest whole number while still keeping the data type consistent.

## Variables

A variable is basically a container that stores data kind of like a labelled box in the kitchen the label stays the same even when whats inside changes. To create one we just give it a name add equals sign and then the value this is called assignment. Best practice is naming it something that actually describes what its for like device_ID instead of something random.

Once a variable is created we can call it just by typing its name and Python will use whatever object is stored inside no quotation marks needed when calling it in print. We can also reassign a variable to a new value anytime and it doesnt even have to be the same data type as before.

If we are ever unsure what type of data is inside a variable we can use the type function which literally returns the data type for us. And if we try to combine two different incompatible types like adding a string and an integer together we get a type error since Python cant merge them like that.

Naming rules I need to remember

- only letters numbers and underscores allowed in variable names
- variable names are case sensitive so time Time TIME are all different
- dont use Python keywords like True False or if as variable names
- separate words with underscores like login_attempts instead of loginattempts
- avoid similar sounding names that could confuse like start_time and starting_time
- keep names descriptive but not unnecessarily long

## Conditional Statements

A conditional statement basically evaluates code to check if certain condition is met and this is what lets automation actually make decisions. It starts with the keyword if followed by the condition we want to check and then a colon after which the action to perform goes on the next line indented at least one space. The first line is called the header and the indented action part is called the body.

We can build conditions using operators like greater than less than greater than or equal less than or equal and for checking if something matches exactly we use double equals not single equals since single equals is for assignment. For checking if two things are not equal we use exclamation mark followed by equals.

If the condition in our if statement is False and we want something else to happen instead we add else after it followed by colon and then the alternate action indented under it. And if there are multiple possible conditions to check we use elif in between if and else Python checks these in order and stops at whichever one evaluates True first unlike multiple if statements where it checks all of them separately.

We can also combine multiple conditions using logical operators

- and requires both sides to be True
- or requires only one side to be True
- not flips the result so True becomes False and False becomes True

## Iterative Statements

Sometimes we dont just want the computer to decide something we want it to repeat a task over and over and thats where iterative statements or loops come in. There are two types for loops and while loops.

For loops repeat code for a specified sequence like going through every item in a list. It starts with keyword for then a loop variable commonly named i then the in operator followed by the sequence to iterate through and ends with colon this is the header. The indented part after is the body which runs for each item in the sequence. We can also combine for loops with the range function which generates a sequence of numbers starting from 0 by default and excluding the stop number so range(10) actually loops 10 times from 0 to 9.

While loops on the other hand repeat based on a condition being True instead of going through a fixed sequence. Unlike for loops the loop variable here is not created inside the loop header itself it has to be assigned before the loop starts. The loop keeps running as long as the condition stays True and stops the moment it becomes False also we have to manually change the loop variable inside the body otherwise it will run forever which is called an infinite loop and we would need to press CTRL-C or CTRL-Z to stop it.

Two more keywords help control loops

- break exits the loop completely once a certain condition is met
- continue skips just that one iteration and moves to the next one

