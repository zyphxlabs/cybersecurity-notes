## Databases and Websites
Basically every website that has a login or a search bar is talking to a database behind the scenes. A database just stores data in a structured way so it can be pulled up modified or added to whenever needed. So when i type my username and password into a login form the site isnt magically knowing if im right or wrong, its sending that off to a database and checking it against whats stored there. Same deal with search, if i search for a book on some shop site it goes and fetches that record from the db and shows it back to me

The thing managing all this on the backend is called a dbms, stuff like mysql postgresql sqlite or ms sql server, and all of these understand sql. So any time an app talks to its database its really just sending sql queries under the hood, we just dont see it happening

## How SQL Injection Actually Works
Lets say theres a login form and i put in John as the username and Un@detectable444 as the password. The website is probably building a query that looks something like this behind the scenes

```sql
SELECT * FROM users WHERE username = 'John' AND password = 'Un@detectable444';
```

Makes sense, both username and password need to match since theyre joined by AND. The issue starts when the site doesnt actually check or clean up whatever i type in. If theres zero validation happening i could type something like this into the password field instead

```
abc' OR 1=1;-- -
```

Now the query the backend builds looks like this

```sql
SELECT * FROM users WHERE username = 'John' AND password = 'abc' OR 1=1;-- -';
```

Password abc obviously fails since thats not the real password, but because theres an OR sitting right after it, the query just needs one side to be true, and 1=1 is always true no matter what. So the whole thing passes even though i had no idea what the actual password was. The -- - at the end just comments out whatever sql was left after my injection so it doesnt throw a syntax error. Honestly the single quote right before OR is doing all the heavy lifting here, without it my input just gets read as one long literal password string, but with it i basically close off the original string early and the rest gets treated as actual sql logic instead of just text

## SQLMap
Doing all this by hand every time is slow, sqlmap basically automates the whole hunt for injection points and exploiting them once found. Comes preinstalled on some distros already, otherwise its a quick install away. Its cli only so everything runs from terminal

sqlmap --help dumps every flag it supports which is honestly a lot. If i dont wanna memorize flags theres a --wizard mode that just walks through it step by step asking questions instead

```
sqlmap --wizard
```

## Testing a URL
If i spot a url with a get parameter like example.com/search?cat=1 thats usually worth testing since that cat=1 value is probably getting dropped straight into a query somewhere. Testing it is just

```
sqlmap -u "http://example.com/search?cat=1"
```

Sqlmap runs through a bunch of checks on its own, connection test waf detection checking if the parameter is even dynamic, then it starts throwing different injection techniques at it. Ended up getting cat flagged as vulnerable to a few types at once

- boolean-based blind — throws in something always true like AND 2175=2175 and watches how the page reacts
- error-based — deliberately breaks the query so the db throws an error, and these errors tend to leak useful info back
- time-based blind — injects something like AND SLEEP(5) and just times the response, if it takes 5 seconds longer thats confirmation even with zero visible change on the page
- union query — tacks on a UNION SELECT to sneak extra data alongside the normal results

It also figures out the backend details on its own like dbms type os and web stack, so no need to guess that stuff manually

## Pulling Databases Tables and Records
Once somethings confirmed vulnerable, --dbs grabs every database name available

```
sqlmap -u "http://example.com/search?cat=1" --dbs
```

From there -D plus --tables lists whats inside a specific database

```
sqlmap -u "http://example.com/search?cat=1" -D users --tables
```

And once i know which table i actually want, -D -T and --dump pulls the real data out of it

```
sqlmap -u "http://example.com/search?cat=1" -D users -T accounts --dump
```

This spits out whatever rows and columns exist there. Kinda cool that if it spots something that looks like a password hash mid dump it actually stops and asks if i want to save it or try cracking it right then with a dictionary attack

## Cookie Based Testing
A lot of real apps arent just sitting wide open, theyre gated behind sessions and cookies. Just hitting a raw url with sqlmap in that case might get me redirected or denied or just show a totally different unauthenticated view. Thats where --cookie comes in, i can grab my session cookie after logging in normally through a browser and hand it straight to sqlmap so it acts like it IS my logged in session

```
sqlmap -u "http://example.com/page" --cookie="SESSIONID=abcdef123456"
```

Pretty much mandatory for testing anything that only shows up once youre actually logged in

## POST Based Testing
Not everything shows its parameters in the url, login and registration forms usually send stuff through the request body via post instead. For these i need to intercept the actual post request first, usually through a proxy, save it to a text file, then just hand that file to sqlmap directly

```
sqlmap -r intercepted_request.txt
```

## Notes From Practicing on a Login Form
Ran into a case where the get parameters werent sitting out in the open in the url like a normal search bar, so i had to go grab them manually. Right click the page hit inspect go to the network tab then actually submit the login form with some junk test creds, that request shows up in network and i can copy the full url with all its params attached, ended up looking something like

```
http://example.com/includes/user_login?email=test&password=test
```

Important thing i almost messed up on, wrapping that url in single quotes when passing it to sqlmap so the terminal doesnt choke on the ? character. Also a plain scan didnt actually catch anything the first time, had to throw --level=5 on the end to force a deeper scan before it actually found the injection

Sqlmap also stops mid scan sometimes to ask questions, these are the answers that got it running smooth for me

- asks if it should skip payloads for other dbms once it thinks the backend is mysql — y
- asks if it should extend tests for mysql using the provided risk value — y
- asks to try a random integer for --union-char since null values didnt work — y
- once a parameter is confirmed vulnerable it asks if i want to keep testing other params — n since i already had what i needed