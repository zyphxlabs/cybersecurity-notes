## Cryptography Basics

Cryptography is basically about keeping a conversation safe even if someone is sitting in the middle watching everything. It protects three things confidentiality so nobody else can read it integrity so nobody can secretly change it and authenticity so you actually know who you are talking to. We use this daily without even noticing like when we login on https our password gets encrypted or when we do online banking the site shows a verified certificate or when we download a file the hash tells us if it got tampered with or not

## Key Terms

- Plaintext is the original message before anything happens to it can be text image anything
- Ciphertext is that same message after it got scrambled
- Cipher is the algorithm that does the scrambling
- Key is the secret value that goes into the cipher to make it work
- Encryption is going from plaintext to ciphertext
- Decryption is going back from ciphertext to plaintext

## XOR

XOR is just asking are these two bits different if yes it gives 1 if no it gives 0 in crypto we use it like C = P ⊕ K to encrypt and P = C ⊕ K to decrypt so the same key that locked it also unlocks it that is why its called symmetric by nature

A few things worth remembering

- A ⊕ A always gives 0
- A ⊕ 0 gives back A
- A ⊕ B is same as B ⊕ A

## Modulo

Modulo is nothing but the remainder left after dividing something like 23 % 6 = 5 because 23 is 3 times 6 plus 5 or 25 % 5 = 0 because it divides fully or 23 % 7 = 2 same idea it does not go back the other way that is why it gets used so much in asymmetric crypto

## Caesar Cipher

Caesar cipher is when you shift every letter by a fixed number like if key is 3 you shift right so CRYPTOGRAPHY becomes FUBSWRJUDSKB and to decrypt you just shift left by the same amount. Its completely broken now because there are only 25 possible keys so anyone can brute force it in seconds its basically dead by todays standards

## Symmetric Encryption

In symmetric encryption one single key does both jobs it encrypts and it decrypts so both people talking need to already have that same key which brings the real problem how do you even share that key safely in the first place

- DES had 56 bit key and got cracked in under 24 hours back in 1999 completely dead now
- 3DES was 168 bit but only 112 bit effective basically DES run three times just an emergency patch not a real fix got deprecated in 2019
- AES comes in 128 192 or 256 bit and is the current standard the one we should actually use

## Asymmetric Encryption

Asymmetric encryption uses two keys public and private and they come as a matched pair. Public key you give to everyone and its used to encrypt while private key you never share and its used to decrypt so if someone encrypts something using your public key only your private key can open it back up

- RSA comes in 2048 3072 or 4096 bit minimum recommended is 2048
- Diffie Hellman also comes in same sizes 2048 3072 4096 minimum recommended 2048
- ECC only needs 256 bit to give strength equal to 3072 bit RSA thats why its used so much on mobile devices

## Symmetric vs Asymmetric

Symmetric uses one shared key and is fast with smaller key size but the problem is sharing that key securely while asymmetric uses a public and private pair and is slower with much bigger keys and the problem there is it being heavier on the CPU AES is the example for symmetric while RSA and ECC are examples for asymmetric

## Why Laws Care About This

Some industries are legally forced to encrypt their data because the risk is too high if they dont

- PCI DSS covers credit card data encrypted both at rest and in transit
- HIPAA and HITECH cover medical records in the US
- GDPR covers personal data in the EU
- DPA covers personal data in the UK