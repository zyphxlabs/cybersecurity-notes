## Strings Recap

String data is basically an ordered sequence of characters and we already know we write them in quotation marks either single or double doesnt matter but this course sticks to double. We can also convert other data types into a string using the str() function like str(123) which turns the integer 123 into a string of three characters this is useful when we want to search through it or slice it since integers cant be sliced like that

## Length And Indices

len() function returns how many elements something has so len("security") gives us 8 because there are 8 characters in that word. As a security person we could use this to check if something like an ip address is a valid length since ipv4 addresses max out at 15 characters

Every character in a string has an index and indexing starts from 0 not 1 so in the string h32rb17 h is at index 0 3 is at index 1 and so on we can also count backwards using negative indices where the last character is -1 and it goes back from there

## Bracket Notation And Slicing

Bracket notation is when we place an index number in square brackets right after a string or variable to pull out a specific character like device_id[0] gives us the first character. If we want more than one character we take a slice by giving two indices separated by a colon like device_id[0:3] this starts at index 0 and goes up to but not including index 3 so it actually gives us characters at 0 1 and 2

- bracket notation single character example "h32rb17"[0] gives h
- slice example "h32rb17"[0:3] gives h32

## Index Method

.index() method finds where a character or substring first shows up in a string and gives back that position. So "h32rb17".index("r") returns 3 because r first appears at index 3. If we search for something that doesnt exist in the string python throws an error instead of returning something

One thing to watch out for is it only returns the first occurrence so if the same letter repeats later in the string it wont tell us about the second one. This applies to substrings too like finding "tshah" inside a bigger string of usernames it gives the starting index of where that substring begins but we gotta be careful cause if we search a shorter version of it like just "ts" it might match somewhere else first and give us wrong index

## Strings Are Immutable

Immutable basically means once a string is created we cant go in and directly change one character of it using index notation if we try python gives an error. So if my_string is "hello" and we try to change the e to an a directly it wont work we would have to create a whole new string instead

## Lists Recap

Lists let us store multiple items together in one variable and we write them with square brackets separating items with commas. Just like strings the first item is at index 0 and we can pull elements out the same way with bracket notation

We can join two lists together using the plus sign this is called list concatenation and it just puts the second list right after the first one. Difference from strings though is lists are not immutable so we can freely change add or remove things in them anytime

## Changing And Modifying Lists

To change a specific element we just use bracket notation on the left side with the index we want then assign a new value to it like my_list[1] = 7 this replaces whatever was at index 1

- insert() adds an element at a specific position and takes two arguments the position and the value everything after that position shifts down by one
- remove() deletes the first occurrence of a specific value we give it directly not an index
- append() adds a new item to the very end of the list

## Algorithms

An algorithm is basically just a set of steps that takes some input does something with it and gives us an output like a solution to a problem. Even everyday stuff like making coffee is technically following an algorithm since we follow the same steps every time

As an example we can write an algorithm to extract the first three digits from a list of ip addresses. First we figure out how to do it for just one address using string slicing then we wrap that solution in a for loop so it runs for every address in the list and we use append() to add each result into a new empty list we made beforehand for storing the answers

## Regular Expressions Intro

A regular expression or regex is basically a pattern made of characters that we use to search through strings for specific stuff like ip addresses emails or device ids. To use regex in python we gotta import the re module first with import re

re.findall() is the main function we use it takes two things the pattern we are searching for and the string we want to search through and it gives back a list of everything that matched. If the pattern is just plain letters or numbers with no special symbols it just looks for that exact match

## Regex Symbols

- \w matches any letter or number and also the underscore
- \d matches any single digit
- \s matches a single whitespace like space tab or newline
- . matches literally any character except newline
- \. matches an actual period character since dot alone means something else in regex

For quantifying how many times something repeats

- + means one or more occurrences so \d+ would match a whole number like 123 not just single digits
- * means zero one or more occurrences so it can also match empty strings which sometimes clutters the results
- {n} means exactly n repetitions like \d{2} matches exactly two digits in a row
- {n,n} means a range like \d{1,3} matches anywhere from one to three digits together

When building a bigger pattern like extracting usernames and login attempts from a string we break the problem into smaller pieces first figure out what each part looks like username colon space then number and represent each with the right symbol then combine them together into one pattern like \w+:\s\d+ this is basically how we construct more complex regex for real data