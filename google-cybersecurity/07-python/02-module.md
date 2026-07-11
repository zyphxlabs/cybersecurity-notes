## Functions Basics

A function is basically a piece of code that we can reuse again and again instead of writing same lines multiple times. Think of it like a dishwasher instead of washing every dish separately it just automates the whole thing for you. Functions save time and if we ever need to change something we just change it in one place and it applies everywhere we use it

There are two types of functions

- built in functions which already exist in python like print()
- user defined functions which we create ourselves for our own needs

## Defining And Calling A Function

To define a function we use the def keyword before the function name followed by parentheses and a colon then the body comes indented below it. Just writing the function does not run it though we also have to call it separately by writing its name with parentheses after it. I tried running just the definition without calling and nothing printed which makes sense because python only knows the function exists it does not run it on its own

example

def greet_employee():
    print("you are logged in")

greet_employee()

one thing to keep in mind is if you call a function inside its own definition without any stopping condition it creates an infinite loop so gotta be careful with that

## Parameters And Arguments

Parameters are the variables we put inside the parentheses when defining the function and arguments are the actual values we pass in when calling that function. So parameter is like the empty slot and argument is what fills that slot. Like in def remaining_login_attempts(maximum_attempts, total_attempts) here maximum_attempts and total_attempts are parameters but when we call it as remaining_login_attempts(3, 2) then 3 and 2 become the arguments and they go in order first value fills first parameter

we can also have functions with multiple parameters separated by commas and same for arguments when calling

## Return Statement

Return is used when we want the function to actually send some information back out instead of just printing it. The keyword return is placed before whatever we want to send back and once python hits a return line it exits the function right there so anything written after return inside that function wont even run

def calculate_fails(total_attempts, failed_attempts):
    fail_percentage = failed_attempts / total_attempts
    return fail_percentage

this is useful because we can store the returned value in a new variable and use it later like in a conditional to check if account should get locked or not based on fail percentage

## Global And Local Variables

Global variable is the one defined outside of any function and it can be accessed anywhere in the program even inside functions. Local variable is the one created inside a function and it only lives inside that function once the function finishes running python deletes it from memory so we cant use it outside

- global variable set once outside a function is usable everywhere
- local variable stays trapped inside the function it was made in

also learned something interesting if we use same variable name inside a function that already exists as global it just creates a whole new local variable with that name and it does not touch the original global one they end up having separate values so its better to avoid using the same name for global and local both cause it gets confusing fast

## Built In Functions

print() takes any number of arguments of any data type separated by commas and just prints them all out

type() tells us the data type of whatever we pass into it but it only takes one argument at a time

max() and min() work on numbers or a list of numbers and give us the largest or smallest value from it. Used this to think about like finding the longest or shortest login session time from a list of session minutes

sorted() arranges the items of a list smallest to largest by default for numbers or alphabetically for strings and the original list does not get changed at all a new sorted version just gets printed or stored separately

- print() many arguments any type
- type() only one argument
- max() largest value
- min() smallest value
- sorted() arranges list does not modify original

also we can pass one function inside another like print(type("security")) here type() runs first and its result goes into print() this is called passing output of one function into another

## Modules And Libraries

Module is basically just a python file that has functions variables classes and other code already written in it. Library is a collection of these modules bundled together

python standard library comes packaged with python itself and has stuff like

- re for searching patterns in log files
- csv for working with csv files
- glob and os for command line interaction
- time and datetime for timestamps
- statistics for stuff like mean() and median()

to use a module we import it with the import keyword like import statistics then we call its functions using statistics.mean() but if we only want specific functions we can do from statistics import mean this way we dont have to type statistics. before it every time

external libraries like beautiful soup for parsing html or numpy for math and arrays are not built in so we gotta install them first before importing usually with pip install then import them normally

## Pep 8 And Comments

PEP 8 is basically like a style guide for python that tells us how to format and write clean code so its consistent and easy for other programmers to read. Its not mandatory but good practice since code gets read way more than it gets written

comments are just notes we leave in code to explain the intention behind it starts with a # symbol for single line and should stay under 79 characters as per pep 8. For longer explanations we use multi line comments either by stacking multiple # lines or by wrapping text in triple quotes """ """ which is called a docstring

indentation is also super important in python it tells python which lines belong together like the body of a function or a loop pep 8 recommends 4 spaces for indentation and if we mess this up either the code wont run right or itll run in a way we didnt intend