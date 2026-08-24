## Cryptographic Failures
This happens when sensitive data isnt properly protected due to a lack of encryption faulty implementation or just insufficient security measures overall. Includes stuff like storing passwords without hashing them, using outdated or weak algorithms like md5 sha1 or des, exposing encryption keys, or failing to secure data while its being transmitted

A really telling example of this is when an application or service decides to roll their own cryptography instead of relying on well established vetted and verifiably secure encryption algorithms that have already been tested by the community

Preventing this starts with picking strong modern algorithms and implementing them the right way. Sensitive stuff like passwords should be hashed using slow robust hashing functions like bcrypt scrypt or argon2. When encrypting data you should never try to invent your own algorithm, always lean on trusted industry standard libraries instead. Access credentials for things like third party services should never be hardcoded into source code config files or repos, they belong in a proper secure key management system built specifically for storing secrets

## Injection
Injection has honestly been around forever on security vulnerability lists and its still a classic form of web exploitation. It happens when an app takes user input and mishandles it, instead of processing that input securely it passes it directly into something that can execute commands or queries like a database a shell a templating engine or an api

Sql injection is probably the most well known form of this, where an attacker sneaks a query into something like a login form and it gets processed directly by the database. This happens because the app fails to sanitise user input and just uses it straight away to build the query, like taking a username field and directly plugging it into a database query without any checks

Some classic types of injection worth knowing

- Sql injection
- Command injection
- Ai prompts
- Server side template injection also known as ssti

Even today these attacks are still extremely relevant which is exactly why injection keeps showing up on vulnerability lists over and over, its considered high severity and should be treated seriously

Preventing injection comes down to always treating user input as untrusted no matter what. For sql queries this means using prepared statements and parameterized queries instead of just concatenating strings together to build a query. For os commands avoid functions that pass input directly into a system shell, rely on safer apis and processes that dont invoke a shell at all. Input validation and sanitisation matter a lot here too, escaping dangerous characters enforcing strict data types and filtering input before the app even processes it goes a long way in preventing this

## Software or Data Integrity Failures
This happens when an app relies on code updates or data that it just assumes is safe without ever verifying its authenticity integrity or where it actually came from. This includes trusting software updates without verifying them, loading scripts or config files from untrusted sources, failing to validate data that affects the apps logic, or accepting stuff like binaries templates or json files without confirming whether theyve been tampered with

Avoiding this starts with establishing clear trust boundaries. An app should never just assume code updates or key pieces of data are legitimate by default, their integrity needs to actually be verified. This usually means using cryptographic checks like checksums for update packages and making sure only trusted sources are able to modify critical artefacts. This kind of integrity and trust boundary thinking should also extend into build processes like ci/cd pipelines, not just the running application itself