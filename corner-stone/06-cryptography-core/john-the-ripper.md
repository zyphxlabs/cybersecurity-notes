## John the Ripper Basics

John the ripper is basically a hash cracking tool thats fast and gets used a lot in CTFs and pentesting it works by hashing a wordlist and comparing each result to your target hash if something matches that means the password is cracked. We should use Jumbo John specifically because it comes with extra tools like zip2john rar2john ssh2john which the basic version doesnt have. Its already pre installed on Kali and AttackBox so just typing john confirms its there

## Wordlist to Use

- always start with rockyou.txt it has 14 million real passwords from a 2009 breach
- location on Kali is /usr/share/wordlists/rockyou.txt
- if rockyou doesnt work there are more wordlists in the SecLists repo

## Basic Syntax

To auto detect the hash type and crack it you just run john hashfile.txt or with a wordlist john --wordlist=/usr/share/wordlists/rockyou.txt hashfile.txt you can also specify the format manually like john --wordlist=/usr/share/wordlists/rockyou.txt --format=raw-md5 hashfile.txt and honestly you should always specify format when you already know it because auto detect can get it wrong sometimes

## Cracking Windows Hashes NTLM

Windows keeps its password hashes in the SAM database and the hash format for this is called NTHash or NTLM to actually get these hashes you need something like mimikatz or access to NTDS.dit. You dont always have to crack them either theres a pass the hash attack option too but cracking still works when the password policy is weak the command for this is john --format=nt --wordlist=/usr/share/wordlists/rockyou.txt ntlm.txt

## Cracking Linux Hashes etc shadow

Linux keeps its hashes in /etc/shadow and only root can read that file we cant feed the shadow file directly into john so we need to combine it with /etc/passwd first using the unshadow tool which comes built into the john suite

```bash
unshadow /etc/passwd /etc/shadow > unshadowed.txt
john --wordlist=/usr/share/wordlists/rockyou.txt --format=sha512crypt unshadowed.txt
```

you dont need the full files either just the relevant lines work fine too the shadow file format goes like $prefix$options$salt$hash and the prefix tells you which algorithm was used for example $6$ means sha512crypt

## Single Crack Mode

Instead of using a wordlist john can use the username itself to generate password guesses this is called word mangling where it takes the username and mutates it so a username like Markus could turn into Markus1 MARkus Markus! markus2 and so on it also pulls info from the GECOS field in /etc/passwd like full name and home directory before running this you need to prepend the username to the hash in the file

```bash
# Change this:
1efee03cdcb96d90ad48ccc7b8666033
# To this:
mike:1efee03cdcb96d90ad48ccc7b8666033

john --single --format=raw-sha256 hashes.txt
```

## Cracking Zip Files

For zip files you use zip2john to convert it into a hash john can actually read then you crack it just like any other hash

```bash
zip2john zipfile.zip > zip_hash.txt
john --wordlist=/usr/share/wordlists/rockyou.txt zip_hash.txt
```

## Cracking RAR Files

Same exact idea as zip except this time its rar2john

```bash
rar2john rarfile.rar > rar_hash.txt
john --wordlist=/usr/share/wordlists/rockyou.txt rar_hash.txt
```

## Cracking SSH Private Key Passwords

SSH private keys like id_rsa can also be password protected so we use ssh2john to extract the hash out of the key file then crack it to get the passphrase and use that key to actually login through SSH

```bash
ssh2john id_rsa > id_rsa_hash.txt
john --wordlist=/usr/share/wordlists/rockyou.txt id_rsa_hash.txt

# If ssh2john not installed:
python3 /opt/john/ssh2john.py id_rsa > id_rsa_hash.txt
```

## Conversion Tools Pattern to Remember

Every file type basically follows the same pattern first convert then crack

- unshadow is for Linux shadow hashes
- zip2john is for password protected Zip files
- rar2john is for password protected RAR files
- ssh2john is for SSH private key passphrases

## Key Things to Remember

You can never decrypt a hash you can only crack it by guessing dictionary attack means hashing every word in a list and comparing it to the target while single crack mode means mangling the username to guess weak passwords. Always identify the hash type before running john because wrong format gives no results GPU is faster than CPU for cracking but VMs cant use the host GPU and bcrypt is designed to resist GPU cracking so its much slower to brute force rockyou.txt still covers most CTF and weak real world passwords