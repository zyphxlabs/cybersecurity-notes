## Web Application Components
A web app can be thought of like a planet, the astronaut exploring it is basically the user browsing it, we only see the surface but theres a lot happening underneath. The whole planet represents the web server with tons of stuff going on that we normally dont see, all we see is the actual pages or app

Front end is basically the surface, the part the user actually sees and interacts with, it uses html css and javascript to work. Html works like the dna of a simple organism, its literally the instructions telling the browser what to display and how. Css is like the part of dna that decides colour shape size and texture, it gives the page its look. Javascript is the brain of a more advanced organism, it lets the page make decisions and do complex stuff based on how the user interacts with it instead of just displaying static info

Back end is everything you dont see in the browser but its what actually keeps the app working, kinda like the gravity and structures that keep a planet functioning. Database is where info gets stored modified and retrieved like a users preferences, on a planet this would be like an inhabitant storing locations in a map or writing in a diary. Infrastructure includes web servers app servers storage networking devices and other software, basically the roads cars and fuel that keep everything moving. WAF or web application firewall is optional and it filters out dangerous requests before they reach the server, kinda like how the atmosphere protects a planet from harmful uv rays

## HTTP Requests
An http request is what a user sends to the web server to make something happen, its usually the first contact point between user and server so its important to understand especially for security

Request line is the first part of the request and it tells the server what kind of request its dealing with, it has three parts method path and version, written as METHOD /path HTTP/version

- GET — fetch data without changing anything, avoid putting sensitive info like tokens or passwords here since it shows as plaintext
- POST — sends data to create or update something, always validate and clean input to avoid sql injection or xss
- PUT — replaces or updates something, make sure user is authorised before accepting
- DELETE — removes something, again only authorised users should be able to do this
- PATCH — updates part of a resource without replacing the whole thing, still needs validation
- HEAD — same as get but only retrieves headers not full content
- OPTIONS — tells you what methods are available for a resource
- TRACE — similar to options mostly used for debugging, a lot of servers disable it for security reasons
- CONNECT — used to create a secure connection like for https

Url path tells the server where to find the resource being asked for, like in myshop.io/api/orders/482 the path api/orders/482 points to a specific order. Attackers try to manipulate this path so its important to validate it sanitise it against injection and protect sensitive data with proper risk assessments

Http version shows which protocol version is used between client and server. Http 0.9 came in 1991 and only supported get requests. Http 1.0 came in 1996 and added headers and better caching. Http 1.1 came in 1997 and brought persistent connections chunked transfer encoding and better caching, its still widely used today. Http 2 came in 2015 and introduced multiplexing header compression and prioritisation for speed. Http 3 came in 2022 and uses a new protocol called quic for faster and more secure connections. Even though 2 and 3 are better a lot of systems still run on 1.1 since its well supported everywhere

## Security Headers
Security headers help protect the web app from stuff like xss and clickjacking. You can check any websites headers using online tools built for that purpose

Content security policy or csp is an extra security layer that helps mitigate xss attacks, it lets admins define what domains or sources are considered safe. The keyword self refers to the same domain the site is hosted on. Say a header looks like default-src self script-src self plus assets.mysite.dev style-src self, default-src sets the default policy to only allow the current site, script-src allows scripts from self and that one trusted asset domain, and style-src restricts css to only load from self

Hsts or strict transport security makes sure browsers always connect over https. In something like max-age=31536000 includeSubDomains preload, max-age is the expiry time in seconds, includeSubDomains applies the rule to all subdomains too, and preload lets the site get added to browser preload lists so https gets enforced even before the first visit

X-Content-Type-Options tells the browser not to guess the mime type of a resource and only trust the content-type header, the directive nosniff is what enforces this

Referrer-Policy controls how much info gets sent to the destination server when a user gets redirected from one site to another. No-referrer disables sending any referrer info at all. Same-origin only sends referrer info when destination is part of the same origin. Strict-origin only sends referrer as origin when protocol stays the same like https to https. Strict-origin-when-cross-origin is similar to strict-origin but sends the full url path when the request is same origin

## URL Anatomy
A url is basically a web address that lets you access stuff online whether its a webpage video photo or other media, it guides the browser to the right place on the internet

Scheme is the protocol used to access the site, most common ones are http and https, https is more secure since it encrypts the connection which is why its recommended and often enforced

User part of a url can sometimes include login details like a username for sites needing authentication, this is rare nowadays since putting credentials in the url isnt safe and can expose sensitive info

Host or domain is the most important part since it tells you which website youre actually accessing, every domain has to be unique and gets registered through domain registrars. From a security angle watch out for domains that look almost real but have small differences, this is called typosquatting and its commonly used in phishing

Port number directs the browser to the right service on the server, its like telling it which doorway to use, ports range from 1 to 65535 but the common ones are 80 for http and 443 for https

Path points to the specific file or page being requested, its like a roadmap showing the browser where to go, these need to be secured so only authorised users reach sensitive resources

Query string starts with a question mark and is often used for search terms or form inputs, since users can modify these it needs to be handled securely to prevent injection attacks

Fragment starts with a hash symbol and points to a specific section of a page like jumping to a heading, users can modify this too so it needs to be checked and cleaned to avoid injection issues

## HTTP Messages
Http messages are packets of data exchanged between the client and the server, understanding them helps understand how requests and responses actually get communicated

There are two types, http requests sent by the user to trigger actions, and http responses sent back by the server in reply

Start line is like the intro of the message, it tells you whether its a request or a response and gives details on how the message should be handled

Headers are key value pairs giving extra info about the message, they help both client and server handle things properly, covering stuff like security and content types

Empty line is a small divider that separates headers from the body, without it the message could get misinterpreted and cause errors

Body is where the actual data lives, in a request it might be form data being sent, in a response its the actual content the user asked for like a webpage or api data

Understanding these messages matters because they're the foundation of how web apps communicate, knowing them helps diagnose issues and also helps implement proper security measures to protect data during transmission

## Request Headers and Body
Request headers give extra info to the server about the request being made

- Host — specifies the name of the server the request is for
- User-Agent — shares info about the browser making the request
- Referer — shows the url the request came from
- Cookie — info the server previously asked the browser to store
- Content-Type — describes the format of data in the request

For requests like post and put where data is being sent to the server, that data sits in the request body. It can be formatted a few different ways

Url encoded format structures data as key=value pairs separated by an ampersand, special characters get percent encoded, like username=raheel&age=22&country=PK

Form data format allows multiple data blocks separated by a boundary string defined in the header itself, this is used for sending binary data like file or image uploads

Json format sends data as name value pairs separated by commas inside curly braces, like username raheel age 22 country PK

Xml format structures data inside opening and closing tags which can be nested inside each other, like wrapping username age and country each in their own tags

## HTTP Responses
When you interact with a web app the server sends back a response to say whether the request worked or something went wrong, this includes a status code and a reason phrase explaining it in human terms

Status line is the first line of every response and gives three things, the http version being used, the status code as a three digit number, and the reason phrase which explains the code in plain words

Status codes fall into five categories

- 100-199 informational, means server got part of the request and is waiting for the rest
- 200-299 successful, means everything worked and server sent back the requested data
- 300-399 redirection, means the resource moved somewhere else usually with a new url given
- 400-499 client error, means theres a problem with the request like wrong url or missing auth
- 500-599 server error, means something broke on the servers end not the clients fault

100 continue means server got the first part and is ready for the rest. 200 ok means the request worked and the resource is being sent back. 301 moved permanently means the resource has a new url now and that should be used going forward. 404 not found means the server couldnt find the resource at that url. 500 internal server error means something went wrong server side and it couldnt process the request

## Response Headers and Body
Response headers are key value pairs that tell the client how to handle the response

Date shows the exact date and time the response was generated, something like a full timestamp with day date month year and timezone

Content-Type tells the client what kind of content its getting like html or json, along with the character set like utf-8 so the browser displays it properly

Server shows what server software is handling the request, its useful for debugging but can also expose info attackers could use so a lot of people hide or remove it

Set-Cookie sends cookies from server to client which the client stores and sends back later, to stay secure these should use the httponly flag so js cant access them and the secure flag so they only go over https

Cache-Control tells the client how long it can cache the response before checking back with the server, no-cache can be used to stop sensitive info from being cached

Location is used in redirection responses to tell the client where to go next, if this can be modified by users it needs proper validation otherwise it opens up open redirect vulnerabilities where attackers redirect users to malicious sites

Response body is where the actual data lives like html json or images that the server sends back, to prevent xss always sanitise and escape user generated content before putting it in the response