## Why Logs Matter
Attackers try to avoid leaving obvious traces, but the security side still manages to piece together how an attack happened and sometimes even who did it. Kinda like a case where cops investigate a break in at some cabin, they find a busted door a collapsed ceiling footprints in the snow outside and maybe some cctv footage from a neighbor. None of those clues alone tell the full story but put together they lead straight back to whoever did it

Same idea applies digitally. Logs are basically the digital version of those footprints, theyre the traces left behind by any activity happening on a system whether its totally normal or something malicious. Tracing an attacker down usually starts with finding and connecting the right logs

## Where Logs Actually Matter
A few key areas where logs pull their weight

- security events monitoring — spotting anomalous behavior in real time as its happening
- incident investigation and forensics — logs hold the actual detail of what happened during an incident, this is what a root cause analysis is usually built off of
- troubleshooting — logs also capture errors so theyre genuinely useful for diagnosing why something broke
- performance monitoring — can give insight into how well an app or system is actually running over time
- auditing and compliance — logs create a clear trail of activity which matters a lot for compliance requirements

## Types of Logs
The real trick with logs isnt finding them, its knowing which category to actually look in instead of drowning in every event a system generates. Say i need to check successful logins from yesterday on a windows box, i dont need to dig through every log type, just the security log covers that specifically. A few main categories worth knowing

- system logs — useful for troubleshooting os level stuff, things like startup shutdown driver loading and system errors
- security logs — the ones that matter most for actual incident work, covers authentication authorization security policy changes and account changes
- application logs — anything tied to a specific app, user interaction app changes updates and app level errors
- audit logs — detailed record of system changes and user events, big for compliance but also genuinely useful during security monitoring
- network logs — incoming and outgoing traffic info, connection logs and firewall logs, useful for both network troubleshooting and incident work
- access logs — tracks access to specific resources like a web server database app or api

Theres more categories than this depending on whatever app or service is generating logs, but these cover most of the common ground

## Windows Event Logs
Windows keeps activity segregated into separate log files by category, same idea as above. Three of the big ones

- application — anything tied to apps running on the system, errors warnings compatibility issues
- system — os level operations, driver and hardware issues startup shutdown info service status
- security — the most important one from a security standpoint, covers stuff like user authentication account changes and security policy changes

Windows has a built in gui called event viewer for browsing these instead of dealing with raw text. Opening it shows the different log categories on the left, clicking into one shows the actual list of logged events, and opening a specific event shows its full detail

Each logged event has a few key fields worth knowing

- description — the actual detail of what happened
- log name — which log file this event came from
- logged — the timestamp of when it happened
- event id — a unique numeric identifier tied to a specific type of activity

Event ids are honestly the fastest way to search for something specific instead of reading through everything manually. Some genuinely useful ones to remember

- 4624 — successful login
- 4625 — failed login attempt
- 4634 — successful logoff
- 4720 — account created
- 4722 — account enabled
- 4724 — password reset attempt
- 4725 — account disabled
- 4726 — account deleted

Theres way more event ids than this but these cover most of the common security relevant activity worth tracking. Event viewer also lets you filter directly by event id instead of scrolling through everything manually, just plug in the id you want like 4624 and it narrows the whole log down to just those matching entries

## Web Server Access Logs
Every request made to a website, whether its just loading a page logging in or uploading something through a form, gets logged by the web server hosting it. These logs capture stuff like the requesting ip the timestamp the request type and the url being hit. A typical access log entry breaks down roughly like this

- ip address — who made the request
- timestamp — exactly when it happened
- http method — what action was requested, like GET
- url — the actual resource being requested
- status code — the servers response result, like 200 for success or 404 for not found
- user agent — info about the requesters browser and os

## Manual Log Analysis Commands
A handful of basic linux commands cover most manual log digging without needing any fancy tooling

cat just dumps a files full content to the terminal, useful for quickly viewing a log file since theyre plain text

```
cat access.log
```

It can also stitch multiple log files together into one, handy since systems often rotate logs into separate files by timeframe

```
cat access1.log access2.log > combined_access.log
```

grep searches for a specific string or pattern inside a file and only shows matching lines, super useful for pulling every entry tied to one specific ip for example

```
grep "192.168.1.1" access.log
```

less is better for actually paging through a big log file one screen at a time instead of getting flooded all at once

```
less access.log
```

Inside less, spacebar moves forward a page and b moves back a page. You can also search directly by typing / followed by whatever pattern youre looking for and hitting enter, then n jumps to the next match and N jumps back to the previous one

## Log Analysis in General
Log analysis is really just the process of pulling meaningful info out of logs, mainly hunting for signs of abnormal or suspicious activity. Trying to eyeball this manually across a massive log file just isnt realistic past a certain point, which is exactly why knowing the right log category and having the right search commands or filters actually matters, it turns an overwhelming wall of text into something you can actually narrow down and investigate properly