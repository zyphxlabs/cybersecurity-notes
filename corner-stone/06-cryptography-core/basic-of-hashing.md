## Hashing Basics

A hash function basically takes any input no matter the size and gives you a fixed size output called a hash value or digest and its one way meaning you can never reverse it back to get the original input. Even if you change a single bit in the input the whole output changes completely. Theres no key involved in this which is what makes it different from encryption

## Common Hash Algorithms

- MD5 is broken dont use it for anything security related
- SHA1 is also broken dont use it either
- SHA256 is the current standard and still considered secure
- Commands used are md5sum sha1sum sha256sum sha512sum
- Output comes in hexadecimal where each byte is 2 hex digits

## Hash Collisions

A collision happens when two completely different inputs end up producing the same hash. MD5 and SHA1 are both vulnerable to engineered collisions so best to avoid both of them a properly designed hash function makes collisions practically impossible to find

## Hashing for Password Storage

Servers are supposed to store the hash of your password not the actual password so when you login it hashes whatever you typed and compares it to the stored hash. Linux keeps these password hashes in /etc/shadow which only root can access while Windows keeps them in SAM and tools like mimikatz can dump them out

### Linux Hash Format

The format goes like $prefix$options$salt$hash and the prefix tells you which algorithm was used

- $y$ is yescrypt the modern default and strongest one
- $2b$ is bcrypt
- $6$ is sha512crypt
- $1$ is md5crypt which is old and weak

### Bad Practices Real Breaches

- RockYou stored passwords in plaintext and ended up leaking 14 million passwords
- Adobe used deprecated encryption plus plaintext hints which made it worse
- LinkedIn used SHA1 with no salting at all

### Secure Password Storage Steps

- Choose a strong algorithm like Argon2 Scrypt Bcrypt or PBKDF2
- Generate a unique random salt for every user
- Combine the password with that salt
- Hash the combined string
- Store the hash value along with the salt the salt itself doesnt need to be secret

## Rainbow Tables

A rainbow table is basically a pre built lookup table that maps hash to plaintext and its used to crack unsalted hashes almost instantly sites like CrackStation keep massive rainbow tables ready for this

### Protection Salting

Salting means adding a unique random value to each password before hashing it so even if two users pick the exact same password their hashes come out different bcrypt and scrypt already handle this salting automatically for you

## Cracking Hashes

You can never decrypt a hash you can only crack it by guessing so the idea is you hash a bunch of possible inputs and compare each to the target hash until one matches

- Hashcat is GPU based and very fast syntax is hashcat -m type -a 0 hashfile wordlist example being hashcat -m 3200 -a 0 hash.txt /usr/share/wordlists/rockyou.txt
- John the Ripper is CPU based and works in VMs right out of the box
- rockyou.txt is the main wordlist and its found at /usr/share/wordlists/rockyou.txt

For identifying a hash you can use the hashID tool or just check the prefix and context matters too like a web app database is likely MD5 while Windows is likely NTLM theres also the Hashcat Example Hashes page as a reference

## Hashing for Integrity

Same input will always give the same output so we use sha256sum file and compare it to the official hash to check if a download is legit and finding duplicate files works the same way if the hash matches the files are identical

## HMAC

HMAC stands for keyed hash message authentication code and it combines a secret key with a hash function so it proves both authenticity meaning who actually sent it and integrity meaning it wasnt altered along the way

## Hashing vs Encoding vs Encryption

- Hashing is one way fixed output and can never be reversed
- Encoding is reversible needs no key and is just a format change like Base64 or UTF-8
- Encryption is reversible needs a key and its whole job is protecting confidentiality