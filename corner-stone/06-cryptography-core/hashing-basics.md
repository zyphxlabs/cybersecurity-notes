# Hashing Basics

## What is a Hash Function?

- Takes any input → produces a fixed-size output (hash value / digest)
- One-way — cannot reverse the output to get the input
- Any single bit change in input = completely different output
- No key involved — different from encryption

## Common Hash Algorithms

- `MD5` — broken, do not use for security
- `SHA1` — broken, do not use for security
- `SHA-256` — current standard, still secure
- Commands: `md5sum`, `sha1sum`, `sha256sum`, `sha512sum`
- Output format: hexadecimal (each byte = 2 hex digits)

## Hash Collisions

- Two different inputs producing the same hash = collision
- MD5 and SHA1 are vulnerable to engineered collisions — avoid both
- Good hash functions make collisions practically impossible

---

## Hashing for Password Storage

- Servers store the hash of your password, not the password itself
- On login: hash what you typed → compare to stored hash
- Linux stores password hashes in `/etc/shadow` (root only)
- Windows stores them in SAM — tools like `mimikatz` can dump them

### Linux Hash Format

- Format: `$prefix$options$salt$hash`
- Common prefixes:
  - `$y$` — yescrypt (modern default, strongest)
  - `$2b$` — bcrypt
  - `$6$` — sha512crypt
  - `$1$` — md5crypt (old, weak)

### Bad Practices (Real Breaches)

- `RockYou` — stored passwords in plaintext → 14M passwords leaked
- `Adobe` — used deprecated encryption + plaintext hints
- `LinkedIn` — used SHA1 with no salting

### Secure Password Storage Steps

1. Choose strong algorithm: `Argon2`, `Scrypt`, `Bcrypt`, or `PBKDF2`
2. Generate a unique random salt per user
3. Combine: `password + salt`
4. Hash the combined string
5. Store: hash value + salt (salt does not need to be secret)

---

## Rainbow Tables

- Pre-built lookup table of hash → plaintext pairs
- Used to crack unsalted hashes instantly
- Sites like CrackStation use massive rainbow tables

### Protection: Salting

- Add a unique random value (salt) to each password before hashing
- Even if two users have the same password, hashes will differ
- Bcrypt and Scrypt handle salting automatically

---

## Cracking Hashes

- You cannot decrypt a hash — you crack it by guessing
- Hash many inputs → compare to target hash → match = found password

### Tools

- `Hashcat` — GPU-based, very fast
  - Syntax: `hashcat -m <type> -a 0 hashfile wordlist`
  - Example: `hashcat -m 3200 -a 0 hash.txt /usr/share/wordlists/rockyou.txt`
- `John the Ripper` — CPU-based, works in VMs out of the box
- `rockyou.txt` — main wordlist, found at `/usr/share/wordlists/rockyou.txt`

### Hash ID

- Use `hashID` tool or check prefixes to identify hash type
- Context matters: web app DB = likely MD5, Windows = likely NTLM
- Reference: Hashcat Example Hashes page

---

## Hashing for Integrity

- Same input always = same output
- Use `sha256sum file` → compare to official hash to verify a download
- Finding duplicate files: same hash = identical files

## HMAC

- Keyed-Hash Message Authentication Code
- Combines a secret key + hash function
- Proves both authenticity (who sent it) and integrity (not altered)

---

## Hashing vs Encoding vs Encryption

- `Hashing` — one-way, fixed output, cannot reverse
- `Encoding` — reversible, no key, just format change (Base64, UTF-8)
- `Encryption` — reversible, requires key, protects confidentiality
