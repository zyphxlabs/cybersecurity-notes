# Software Basics

## Data Representation  
 
RGB:
Colors are made of Red, Green, Blue.
Each value is 0 to 255.
rgb(255, 0, 0) = red
rgb(0, 0, 0) = black
rgb(255, 255, 255) = white

Everything in a computer is stored as binary — just 0s and 1s.
1 bit = single 0 or 1
8 bits = 1 byte

Binary example:
00001010 = 10 in decimal

Hexadecimal:
Uses 0-9 and A-F
FF = 255 in decimal
You see hex everywhere in cybersecurity — memory addresses, hashes

Octal:
Uses digits 0-7 only
Converts binary by grouping into 3 bits

## Data Encoding
Encoding converts data from one format to another.
Not encryption — anyone can decode it.

ASCII:
Maps characters to numbers
A = 65, B = 66, a = 97
How computers store text as numbers

## Python Basics
Most used language in cybersecurity.
Used for writing tools, automating tasks, parsing logs.

print("hello") — output text
name = "zyphxlabs" — store a variable
if x > 5: — make a decision
for i in range(5): — repeat something
def myfunction(): — create reusable code

## JavaScript Basics
Runs inside the browser.
Makes websites interactive.

console.log("hello") — output to browser console

## Database SQL Basics
SQL is how we talk to databases.
Databases store everything — users, passwords, posts.

SELECT * FROM users — get all users
SELECT * FROM users WHERE username='admin' — get one user
INSERT INTO users VALUES ('zyphxlabs', 'pass') — add a record
UPDATE users SET password='new' WHERE username='zyphxlabs' — update
DELETE FROM users WHERE username='zyphxlabs' — delete
