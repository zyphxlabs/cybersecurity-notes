## Public Key Cryptography Basics

Symmetric encryption only really gives you confidentiality but it doesnt tell you who you are actually talking to thats where asymmetric or public key crypto comes in it handles authentication authenticity and integrity as well so the real problem it solves is how do you verify who is on the other end when you are talking to someone online

The four goals it covers are

- Authentication is this really them
- Authenticity did this message really come from them
- Integrity was this message altered while in transit
- Confidentiality can only the right person actually read this

## RSA

RSA works on the idea that its easy to multiply two large prime numbers together but nearly impossible to factor that result back apart. Public key is used to encrypt and private key is used to decrypt

For CTFs you gotta know these variables

- p and q are the two large primes
- n is p times q
- e is the public exponent
- d is the private exponent
- m is plaintext and c is ciphertext
- public key is (n, e) and private key is (n, d)

Main tool for CTF is RsaCtfTool and rsatool works as a backup

## Diffie Hellman Key Exchange

This is basically how two people can agree on a shared key without ever actually sending that key across the network. Both sides pick their own private number then exchange calculated public values and both end up landing on the exact same shared secret on their own even if someone is watching the whole exchange they cant derive the secret from it. Its mainly used just for the key exchange part and then everyone switches to faster symmetric encryption after that its often paired with RSA where DH handles the key exchange and RSA handles identity verification

## SSH Keys

When you connect to a server the first time it sends you its public key fingerprint and you have to confirm it once accepted it gets stored in ~/.ssh/known_hosts. Client authentication happens through a key pair instead of a password the public key goes on the servers ~/.ssh/authorized_keys while the private key stays only on your machine and should never be shared

- ssh-keygen -t ed25519 generates the key pair
- ssh -i keyfile user@host connects using a specific key
- private key permissions must be set to 600
- a passphrase encrypts the key locally and its never actually sent to the server

## Digital Signatures

You sign something with your private key and anyone can verify it using your public key the process is you hash the document then encrypt that hash with the private key and send both together the receiver decrypts the hash and compares it if it matches that means its authentic and untampered. Just pasting an image of a signature is not a digital signature at all

## SSL TLS Certificates

HTTPS uses certificates to prove that a site is actually real there is a chain of trust that goes root CA to organisation to certificate and your browser already trusts these root CAs by default. Lets Encrypt is a good example that gives out free TLS certs

## PGP GPG

PGP is used to encrypt files and also do digital signing while GPG is basically the open source version of PGP

- gpg --full-gen-key generates a key pair
- gpg --import backup.key imports a key
- gpg --decrypt file.gpg decrypts a file
- for CTF you can crack the passphrase using gpg2john piped into john

## Key Terms

- Cryptanalysis is the science of trying to break crypto systems
- Brute force means trying every single possible key
- Dictionary attack means trying common words instead of every combination