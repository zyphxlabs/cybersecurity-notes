# John the Ripper Basics

## What is it?

- A hash cracking tool — fast, widely used in CTFs and pentesting
- Works by hashing a wordlist and comparing each result to your target hash
- If it matches, the password is cracked
- Use Jumbo John specifically — it includes extra tools like zip2john,
  rar2john, ssh2john that the basic version doesn't have
- Pre-installed on Kali and AttackBox — just type `john` to confirm

## Wordlist to Use

- Always start with `rockyou.txt` — 14 million real passwords from a 2009 breach
- Location on Kali: `/usr/share/wordlists/rockyou.txt`
- More wordlists available in SecLists repo if rockyou doesn't work

---

## Basic Syntax

- Auto-detect hash type and crack: `john hashfile.txt`
- With wordlist: `john --wordlist=/usr/share/wordlists/rockyou.txt hashfile.txt`
- Specify format manually: `john --wordlist=/usr/share/wordlists/rockyou.txt --format=raw-md5 hashfile.txt`
- Always specify format when you know it — auto-detect can get it wrong

---

## Cracking Windows Hashes (NTLM)

- Windows stores password hashes in the SAM database
- Hash format is called NTHash or NTLM
- To get these hashes you need tools like `mimikatz` or access to `NTDS.dit`
- You don't always need to crack them — "pass the hash" attack is an option
  but cracking works when password policy is weak
- Command: `john --format=nt --wordlist=/usr/share/wordlists/rockyou.txt ntlm.txt`

---

## Cracking Linux Hashes (/etc/shadow)

- Linux stores hashes in `/etc/shadow` — only root can read it
- Can't feed shadow file directly to John — need to combine it with
  `/etc/passwd` first using the `unshadow` tool
- `unshadow` is built into John suite

```bash
unshadow /etc/passwd /etc/shadow > unshadowed.txt
john --wordlist=/usr/share/wordlists/rockyou.txt --format=sha512crypt unshadowed.txt
```

- You can use just the relevant lines from each file instead of the full files
- Shadow file format: `$prefix$options$salt$hash` — prefix tells you the
  algorithm e.g. `$6$` = sha512crypt

---

## Single Crack Mode

- Instead of a wordlist, John uses the username to generate password guesses
- Called word mangling — takes the username and mutates it
- Example: username "Markus" → tries Markus1, MARkus, Markus!, markus2 etc.
- Also uses GECOS field info from /etc/passwd like full name, home directory
- You need to prepend the username to the hash in the file before running

```bash
# Change this:
1efee03cdcb96d90ad48ccc7b8666033
# To this:
mike:1efee03cdcb96d90ad48ccc7b8666033

john --single --format=raw-sha256 hashes.txt
```

---

## Cracking Zip Files

- Use `zip2john` to convert the zip into a hash John can read
- Then crack it the same way as any other hash

```bash
zip2john zipfile.zip > zip_hash.txt
john --wordlist=/usr/share/wordlists/rockyou.txt zip_hash.txt
```

---

## Cracking RAR Files

- Same idea as zip but with `rar2john`

```bash
rar2john rarfile.rar > rar_hash.txt
john --wordlist=/usr/share/wordlists/rockyou.txt rar_hash.txt
```

---

## Cracking SSH Private Key Passwords

- SSH private keys (`id_rsa`) can be password protected
- Use `ssh2john` to extract the hash from the key file
- Then crack it to get the passphrase and use the key for SSH login

```bash
ssh2john id_rsa > id_rsa_hash.txt
john --wordlist=/usr/share/wordlists/rockyou.txt id_rsa_hash.txt

# If ssh2john not installed:
python3 /opt/john/ssh2john.py id_rsa > id_rsa_hash.txt
```

---

## Conversion Tools — Pattern to Remember

- Every file type follows the same pattern: convert first, then crack
- `unshadow` → Linux shadow hashes
- `zip2john` → password protected Zip files
- `rar2john` → password protected RAR files
- `ssh2john` → SSH private key passphrases

---

## Key Things to Remember

- You cannot decrypt a hash — you can only crack it by guessing
- Dictionary attack = hash every word in a list, compare to target
- Single crack mode = mangle the username to guess weak passwords
- Always identify the hash type before running John — wrong format = no results
- GPU is faster than CPU for cracking but VMs can't use host GPU
- Bcrypt is designed to resist GPU cracking — much slower to brute force
- `rockyou.txt` covers most CTF and weak real-world passwords