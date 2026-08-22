## IAAA Basics
Iaaa is a simple way to think about how users and their actions get verified in an application, its basically four layers and you cant skip one to get to the next, each one depends on the previous being done properly

- Identity — the unique account like a user id or email that represents a person or service
- Authentication — actually proving that identity through stuff like passwords otp or passkeys
- Authorisation — defining what that identity is allowed to actually do once verified
- Accountability — recording and alerting on who did what when and from where

Weaknesses in how iaaa gets implemented can be pretty damaging since it can let an attacker either access other peoples data or gain more privileges than they should have. A lot of the owasp top ten categories tie directly back to failures somewhere in this chain

## Broken Access Control
This happens when the server doesnt properly check who is allowed to access what on every single request. A really common example is idor which stands for insecure direct object reference, basically if you can just change an id in the url like going from id=7 to id=6 and suddenly youre seeing or editing someone elses data, that means access control is broken

This usually shows up in two forms, horizontal privilege escalation where youre still the same role but accessing someone elses data, or vertical privilege escalation where you jump up to admin only actions you shouldnt have access to. Both happen because the application is trusting the client side too much instead of enforcing checks server side

Playing around with an accountID value in a url and being able to see other peoples account balances just by changing the number is a textbook example of this, the fix is enforcing proper server side checks on every request instead of assuming the client will only ever request their own data

## Authentication Failures
This is when an application cant reliably verify or bind a users identity properly. Common issues include

- Username enumeration — being able to tell whether a username exists based on how the app responds
- Weak or guessable passwords — especially when theres no lockout or rate limiting to stop brute forcing
- Logic flaws in login or registration flow — like inconsistent handling of usernames
- Insecure session or cookie handling — sessions that dont rotate or get bound to the wrong account

One sneaky example of a logic flaw is registering a username with mixed case like aDmiN when the real admin account is just admin, if the app doesnt normalize usernames properly this can end up letting you log into or clash with the actual admin account. The core issue is the app not treating usernames as case insensitive or canonical when it should

## Logging and Alerting Failures
When an app doesnt properly log or alert on security relevant events defenders basically have no way to detect or investigate an attack after the fact. Good logging is really what accountability depends on, being able to prove who did what and when

In practice this failure shows up as missing authentication events, vague error logs that dont give you enough context, no alerting on stuff like repeated failed logins or privilege changes, short log retention windows, or logs being stored somewhere an attacker could tamper with them. Investigating an attack becomes way harder or sometimes impossible if key pieces of this logging information are missing, which is exactly why proper logging matters so much for accountability

## Key Takeaways
- Broken access control gets fixed by enforcing server side checks on every single request instead of trusting the client
- Authentication failures get addressed by enforcing unique indexes on the canonical form of usernames, rate limiting or locking out brute force attempts, and rotating sessions whenever a password or privilege changes
- Logging and alerting failures get addressed by logging the full auth lifecycle including failed and successful attempts password and role changes and admin actions, centralizing logs off host with proper retention, and alerting on anomalies like brute force bursts or sudden privilege elevation