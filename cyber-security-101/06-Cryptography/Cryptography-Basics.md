# Cryptography Basics


---


## What is Cryptography?

Cryptography = keeping communication secure even when someone is watching.

It protects 3 things:
- **Confidentiality** — nobody else can read it
- **Integrity** — nobody can tamper with it
- **Authenticity** — you know who you're talking to

Real examples we use daily:
- HTTPS login → credentials encrypted
- Online banking → server certificate verified
- File download → hash confirms nothing was changed

---

## Key Terms

| Term | What It Means |
|------|--------------|
| **Plaintext** | Original readable message — text, image, anything |
| **Ciphertext** | The scrambled unreadable version |
| **Cipher** | The algorithm doing the scrambling |
| **Key** | The secret value fed into the cipher |
| **Encryption** | Plaintext → Ciphertext |
| **Decryption** | Ciphertext → Plaintext |

---

## The Math Behind Crypto

### XOR (`⊕`)
"Are these two bits different?" — Yes = 1, No = 0

| A | B | A ⊕ B |
|---|---|-------|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

How it works in crypto:
- Encrypt: `C = P ⊕ K`
- Decrypt: `P = C ⊕ K`

Same key encrypts and decrypts. That makes it symmetric by nature.

Key properties:
- `A ⊕ A = 0`
- `A ⊕ 0 = A`
- `A ⊕ B = B ⊕ A`

### Modulo (`%`)
Remainder after division. That's it.

- `23 % 6 = 5` → 23 = (3 × 6) + 5
- `25 % 5 = 0` → 25 = (5 × 5) + 0
- `23 % 7 = 2` → 23 = (3 × 7) + 2

Not reversible — used heavily in asymmetric crypto.

---

## Caesar Cipher

Shift every letter by a fixed number.

- Key = 3, shift right: `CRYPTOGRAPHY → FUBSWRJUDSKB`
- To decrypt: shift left by 3

**Why it's broken:** Only 25 possible keys. Brute forceable in seconds. Dead by modern standards.

---

## Symmetric Encryption

One key does both — encrypts and decrypts. Both sides need the same key.

**Main problem:** How do you securely share the key in the first place?

| Cipher | Key Size | Notes |
|--------|----------|-------|
| DES | 56-bit | Cracked in under 24 hours in 1999. Dead. |
| 3DES | 168-bit (112-bit effective) | DES run 3 times. Emergency patch. Deprecated 2019. |
| AES | 128 / 192 / 256-bit | Current standard. Use this. |

**Key thing I noted:** 3DES was never a proper fix — just a panic patch. AES replaced it properly.

---

## Asymmetric Encryption

Two keys — public and private. They're a matched pair.

- **Public key** → share with everyone → used to **encrypt**
- **Private key** → never leaves you → used to **decrypt**

Someone encrypts with your public key → only your private key can open it.

| Cipher | Key Size | Notes |
|--------|----------|-------|
| RSA | 2048 / 3072 / 4096-bit | Min recommended: 2048-bit |
| Diffie-Hellman | 2048 / 3072 / 4096-bit | Min recommended: 2048-bit |
| ECC | 256-bit | 256-bit ECC ≈ 3072-bit RSA strength |

**Key thing I noted:** ECC gives same security with much smaller keys — that's why it's used on mobile.

---

## Symmetric vs Asymmetric

| | Symmetric | Asymmetric |
|--|-----------|------------|
| Keys | 1 shared key | Public + Private pair |
| Speed | Fast | Slow |
| Key size | Smaller | Much larger |
| Main problem | Sharing the key securely | Slower, heavier on CPU |
| Example | AES | RSA, ECC |

---

## Why Laws Care About This

Some industries are legally required to encrypt data:

- **PCI DSS** — credit card data, encrypted at rest and in transit
- **HIPAA / HITECH** — medical records in the US
- **GDPR** — personal data in the EU
- **DPA** — personal data in the UK