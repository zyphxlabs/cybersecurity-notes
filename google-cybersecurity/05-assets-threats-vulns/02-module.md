## Security controls and information privacy

Security controls are basically safeguards that reduce specific risks they protect assets before during and after something happens they come in three types

- technical controls which are actual technologies like encryption and authentication systems
- operational controls which are day to day stuff people do like awareness training and incident response
- managerial controls which are more about policies standards and procedures that guide the other two

information privacy is about protection from unauthorized access and distribution of data basically its about people having the right to choose when how and how much of their info gets shared like if you book a flight and give your card info the marketing guy at that airline company shouldnt be able to see it only support agent should and only while helping you thats basically least privilege in action

security controls work well when they know the difference between data owner and data custodian data owner is the person deciding who can access edit use or destroy the info data custodian is anyone or anything responsible for safely storing and handling that data even systems count as custodians not just people

## Cryptography basics

PII is personally identifiable information basically anything that can be used to figure out who you are like your name medical info financial info photos emails or fingerprints protecting this online is hard and thats where cryptography comes in

cryptography is just transforming info into something unreadable for people who arent supposed to see it works in two steps encryption to hide it and decryption to unhide it plaintext is the readable version ciphertext is the scrambled unreadable version

one of the oldest methods is caesars cipher named after julius caesar he used it to send secret messages to his generals it just shifts letters forward by a fixed number so a shift of 3 turns hello into khoor problem is its way too easy to crack since english only has 26 letters you can just brute force all shifts to find it

a cipher is basically the algorithm doing the encrypting and a cryptographic key is what tells you how to decrypt it back caesars cipher had two big flaws the cipher itself was weak and it relied on just a single key so if that key got lost or stolen anyone could read your messages this is why we moved to way more complex encryption methods later

## Symmetric and asymmetric encryption

Encryption these days mainly comes in two types

- symmetric encryption uses a single secret key both sides need to know it to lock and unlock the message
- asymmetric encryption uses two keys public and private public one encrypts data and private one decrypts it only the owner has the private key

symmetric is faster but less secure since sharing that one key is risky asymmetric is slower but more secure since the private key never has to be shared this is why alot of apps use asymmetric to first establish the connection then switch to symmetric once its established for speed

key length matters alot here longer keys mean more possible combos so its harder to brute force but also means slower processing

some common algorithms

- triple DES also called 3DES applies DES three times using three different 56 bit keys giving effective length of 168 bits companies are moving away from it tho
- AES is one of most secure symmetric ones today with keys of 128 192 or 256 bits estimated that brute forcing even a 128 bit AES key would take billions of years
- RSA is asymmetric named after its creators from MIT key sizes go up to 4096 bits mainly used for very sensitive data
- DSA also asymmetric introduced by NIST in early 90s often used alongside RSA in PKI

kerckhoffs principle says a cipher should stay secure even if everyone knows how it works except the key basically security by obscurity is not real security

there was also a vulnerability called heartbleed found in openssl back in 2014 it exposed sensitive data from memory of websites this shows why keeping your encryption software updated actually matters

## Public key infrastructure PKI

PKI is basically the framework that makes secure exchange of info online possible its a two step process first is the actual exchange using symmetric or asymmetric encryption or both second step is establishing trust using digital certificates

digital certificate is basically like a digital ID it proves the identity of a public key holder when a business wants one they send their info to a certificate authority or CA the CA verifies it and encrypts it with their own private key then issues the certificate this way when two systems talk to each other they can trust that the other side is who they claim to be

## Hash functions

Hash function is an algorithm that turns data into a code that cant be decrypted unlike encryption it doesnt give you a way back to original data its a one way process resulting value is called hash value or digest

if even one character changes in the source file the hash value changes completely thats how we check if a file has been tampered with by comparing hash values before and after

MD5 was one of the earliest hash functions made by ronald rivest at MIT in early 90s it produces 128 bit value shown as 32 character string but MD5 had a big flaw called hash collision this is when two different inputs somehow produce the same hash value which is bad because hashes are supposed to be unique identifiers

to fix that we moved to SHA family of algorithms approved by NIST these include

- SHA-1
- SHA-224
- SHA-256
- SHA-384
- SHA-512

all except SHA-1 are considered collision resistant

hashing is also used to store passwords safely since hash cant be reversed even if attacker steals the database they cant get the actual password back but theres a trick against this called rainbow table which is basically a pre made dictionary of hash values mapped to plaintext passwords attackers use this to crack weak hashes

to defend against rainbow tables we use salting which means adding a random string to the data before hashing it so even same passwords end up with totally different hash values making rainbow tables useless against them

## Authentication authorization and accounting AAA

Access controls manage access authorization and accountability of info they work under a framework called AAA which stands for authentication authorization and accounting

authentication is literally just asking who are you it can be based on three factors

- knowledge something you know like password
- ownership something you have like a one time passcode OTP
- characteristic something you are like fingerprint or face scan

single sign on or SSO combines multiple logins into one so you dont have to authenticate again and again but its risky if used alone since if that one login gets compromised everything is exposed thats where multi factor authentication MFA comes in requiring two or more factors together SSO and MFA together give speed and security both

authorization is about what you are allowed to do once youre verified this is where principle of least privilege and separation of duties come in least privilege means give minimum access needed separation of duties means dont let one person have so much control that they can misuse the system like the person doing customer service shouldnt also be the one rating their own performance

common tools for authorization over network

- HTTP basic auth which sends user info everytime but its old and insecure since it sends stuff in plain text
- HTTPS which is the secure version of it
- OAuth which is open standard protocol using API tokens instead of sending username password directly example is signing into a site using your google account without exposing your actual google password

accounting is the last part of AAA its literally about monitoring access logs who accessed what and when this is super important for investigating incidents like breaches everytime someone accesses a system a session starts a session id gets created which is a unique token tied to user and device along with session cookies which help site know how long session should last

if attacker steals your session cookie they can hijack your session and pretend to be you this is called session hijacking its dangerous because they dont even need your password they just need the stolen session token to gain access which is why monitoring logs for weird activity is so important

## Identity and access management IAM

IAM is basically a collection of processes and tech that helps manage digital identities within an org similar to AAA but slightly different structure includes authentication user provisioning and authorization

user provisioning means creating and maintaining someones digital identity like when new employee joins and gets an account with proper access deprovisioning is the opposite removing access once its no longer needed which analysts are also responsible for

for granting authorization there are three common models

- mandatory access control MAC strictest one access given manually by central authority mostly used in military or government
- discretionary access control DAC data owner decides who gets access like sharing a google drive file
- role based access control RBAC access depends on your role in the org like marketing person gets access to analytics but not network admin stuff

## Data lifecycle and governance

Data lifecycle is basically the five stages data goes through in an org

- collect
- store
- use
- archive
- destroy

data governance is the set of processes that define how an org manages its data through this lifecycle it usually involves three roles

- data owner decides who can access edit use or destroy info
- data custodian responsible for safe handling storage and transport of the data
- data steward maintains and implements the actual governance policies

there are also specific types of legally protected data

- PII personally identifiable info anything that can identify you
- PHI protected health info regulated by HIPAA in US and GDPR in EU
- SPII sensitive PII stuff like bank account number or login credentials that need stricter handling

## Privacy regulations and compliance

Information privacy and information security are related but not same privacy is about giving people control over their data security is about actually protecting that data from threats

three major regulations to know

- GDPR made by EU gives people full control over their personal data applies to any business handling EU citizens data no matter where the business is located
- PCI DSS standards for securing credit and debit card transactions made by financial industry orgs
- HIPAA US law protecting patient health info prevents disclosure without consent

to actually check if a company is following these rules there are two ongoing processes

- security audit reviewing controls policies and procedures against expectations usually done once a year
- security assessment checking how resilient current setup is against threats usually done every three to six months mostly by internal teams as prep before the actual audit