## Integrating JS into HTML
JS isnt used to render content on its own, it works together with html and css to make pages dynamic and interactive. Once the html elements exist js is what adds the interactive stuff like validation onclick actions animations and all that. There are two ways to add js into a page, internal and external

Internal js means the code sits directly inside the html file between script tags, this is easier for beginners since you can see the script and the html together in one place and understand how they interact. The script tag can go in the head if it needs to load before the page content, or in the body if its meant to interact with elements as theyre loaded on the page. A basic example is a page with a p tag with id result, then inside a script tag you declare x as 5 and y as 10 add them into result and use document.getElementById("result").innerHTML to push the answer into that p tag, so when the browser loads the file it runs the script and shows the result right there

External js means the js code lives in a separate file with a .js extension, this keeps the html clean and organised especially useful on bigger projects. The external file can be hosted on the same server as the html or somewhere else entirely like a cdn or external server. Same example as above but this time the addition logic sits in a file called script.js and the html just links to it using the src attribute inside the script tag instead of writing the code directly inline, the browser fetches that file and runs it when the page loads, output ends up being exactly the same as the internal version just organised differently

To check whether a site is using internal or external js you just right click and view the page source. If you see a script tag with actual code written inside it thats internal js, if you see a script tag with a src attribute pointing to a file thats external js being pulled in. This is a basic thing to check when pentesting a web app since it tells you where the actual logic is coming from and whether it needs to be fetched separately to analyze it

## Variables Data Types and Functions
Variables are just containers to store values, kinda like labeling a bucket so you know whats inside it later and can reference it again. In js you can declare variables with var let or const. Var is function scoped while let and const are block scoped which gives more control over exactly where a variable is visible inside the code

Data types define what kind of value a variable is actually holding

- string — text values
- number — numeric values
- boolean — true or false
- null and undefined — empty or unassigned values
- object — more complex data like arrays or objects

Functions are just a block of code built to do one specific task, you group logic that repeats into one function instead of rewriting it everywhere. Like say youre building a page that needs to print student results, instead of writing the same print logic for every student you make a function PrintResult(rollNum) that takes the roll number as an argument and shows a message saying that student passed, then you just call this function whenever you need it with whatever roll number youre working with at that moment

## Loops
Loops let you run the same block of code multiple times as long as a condition stays true. For while and do while are the common ones in js, theyre mainly used for repeating tasks like going through a list of items one by one. So instead of calling PrintResult manually 100 separate times you just write a for loop starting i at 0 going up to 100 and call PrintResult(rollNumbers[i]) inside it, this does the exact same job as writing it out 100 times but with way less code, worth noting if the array only actually has 3 roll numbers in it the rest of the calls after index 2 would just be undefined

## Request Response Cycle
This is basically when the browser as the client sends a request to a web server and the server sends back whatever was asked for, could be a webpage data or some other resource, this whole request response flow is the backbone of how basically every website works

## Writing First JS Program
Js is an interpreted language which means the browser executes the code directly without needing to compile it first. We use the Google Chrome console to run js without needing extra tools, you open it with ctrl shift i or by right clicking anywhere on the page and choosing inspect then clicking on the console tab

A basic hello world example is just console.log("Hello, World!") which prints straight to the console. Building on that you can declare a variable like let age = 25 then use an if else to check if age is 18 or above and log either "You are an adult." or "You are a minor." depending on the result, and functions work here too like a greet(name) function that logs "Hello, " plus whatever name you pass into it

For the numbers example specifically you declare x as 5 and y as 10 add them into a variable called result then use console.log to print "The result is: " plus result to the console. Console.log just prints to the developer console rather than popping up a visible alert box on the page itself, its mainly meant for us to check output while writing and testing code

## Dialogue Functions
Js gives us built in functions to interact with the user directly through popup boxes, these are useful for basic interaction but can also get abused if not handled properly which ties into stuff like xss later on

Alert shows a message in a dialogue box with just an ok button, mainly used to convey info or warnings to the user, typing something like alert("Hello THM") in the console pops up a box with that exact message

Prompt asks the user for input through a dialogue box and returns whatever they typed once they click ok, or returns null if they hit cancel instead. As an example you can do name = prompt("What is your name?") then alert("Hello " + name), this asks for a name then greets the user back with whatever they entered

Confirm shows a message with two buttons ok and cancel, it returns true if the user clicks ok and false if they click cancel, something like confirm("Are you sure?") would pop up asking for that yes or no style confirmation and give you a boolean back depending on the choice made

## How Hackers Exploit Dialogue Functions
Imagine getting an email with an html file attached that looks harmless but actually has js inside that messes with your browsing. A simple example is a for loop running from 0 to 3 that calls alert("Hacked") each time, opening this file pops up the Hacked message three times in a row which is already annoying on its own

Now imagine that same loop but set to run 500 times instead of 3, youd be stuck closing popup after popup with no real way to stop it quickly. Its a pretty basic trick but it shows exactly why you should never open js files or html files from sources you dont trust, something this simple can already ruin your whole browsing experience

## Control Flow
Control flow decides the order in which code actually runs based on certain conditions being met. Js gives us if else and switch statements for making decisions, and loops like for while and do while for repeating actions, using these properly is what lets a program handle different situations correctly instead of just running the same way every time

A practical example is asking for someones age through a prompt, then checking with if age is greater than or equal to 18 it updates a message element on the page saying "You are an adult.", otherwise the else block runs and shows "You are a minor." instead. The whole outcome just depends on that one condition check against the age value that was entered into the prompt

## Bypassing Login Forms
Say a developer builds login logic entirely in js, where it only lets someone in if the username is admin and the password matches some specific value thats hardcoded in the script. Opening a page like this in the browser prompts you for a username and password and if you enter the right ones it shows a message confirming youre logged in

The problem here is this whole check is happening client side, which means the logic and possibly even the actual credentials are sitting right there in the page source for anyone to view and read, making it way easier to bypass compared to if the check was actually being done server side where the user cant see or touch the logic at all

## Minified and Obfuscated Files
Minification strips out all the unnecessary stuff from js like spaces line breaks comments and even shortens variable names down to nothing meaningful, this makes the file smaller and faster to load which matters a lot in production environments. It still works exactly the same as before, just way harder for an actual human to read through

Obfuscation goes a step further by intentionally renaming variables and functions to meaningless junk and even inserting dummy code that does nothing useful, the whole point is to make it harder for someone to understand the actual logic if they try reading it. As an example a simple hi() function that just shows an alert saying "Welcome to THM" can get turned into a giant wall of stuff like hex values weird array lookups and functions calling functions that call other functions, total gibberish to look at but when you actually run it in the browser it behaves exactly the same and still shows that same alert message

You can also deobfuscate code using online tools which take that gibberish and turn it back into something much closer to the original readable version. So obfuscation definitely slows an attacker down and adds effort but it doesnt fully stop someone determined enough from eventually reverse engineering the original logic

## Best Practices
- Never rely only on client side validation since a user can disable or manipulate js themselves, server side validation is essential too
- Dont blindly include untrusted libraries through the src attribute, bad actors upload libraries with names that look almost identical to legit ones
- Never hardcode secrets like api keys tokens or credentials into js code, something like const privateAPIKey = 'pk_TryHackMe-1337' is a bad practice since anyone can just view the source and grab it directly
- Always minify and obfuscate js code before using it in production, it reduces file size improves load time and makes it harder for an attacker to understand the logic, they can still eventually reverse engineer it but itll cost them real effort to get there