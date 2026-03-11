# Asymmetric Encryption Lab — RSA Encryption using OpenSSL

## Overview
This lab demonstrates asymmetric encryption using the RSA algorithm via OpenSSL on Kali Linux. Asymmetric encryption uses a key pair — a public key for encryption and a private key for decryption.

---

## Environment
- **OS:** Kali Linux
- **Tool:** OpenSSL
- **Algorithm:** RSA-2048

---

## What is Asymmetric Encryption?
Asymmetric encryption uses two mathematically related keys:
- **Public Key** — shared openly, used to encrypt data
- **Private Key** — kept secret, used to decrypt data

A message encrypted with the public key can only be decrypted with the corresponding private key. A common example is **RSA (Rivest–Shamir–Adleman)**.

---

## Steps

### Step 1 — Generate a Private Key
A 2048-bit RSA private key was generated:
```bash
openssl genpkey -algorithm RSA -out private.pem -pkeyopt rsa_keygen_bits:2048
cat private.pem
```
![Private Key](private_key.png)

---

### Step 2 — Extract the Public Key
The public key was extracted from the private key:
```bash
openssl rsa -in private.pem -pubout -out public.pem
cat public.pem
```
![Public Key](public_key.png)

---

### Step 3 — Encrypt using the Public Key
The plaintext file was encrypted using the public key:
```bash
openssl pkeyutl -encrypt -inkey public.pem -pubin -in mygoal.txt -out mygoal_rsa.enc
```
![Encrypted File](encrypted_file.png)

---

### Step 4 — Decrypt using the Private Key
The encrypted file was decrypted using the private key:
```bash
openssl pkeyutl -decrypt -inkey private.pem -in mygoal_rsa.enc -out mygoal_rsa_decrypted.txt
cat mygoal_rsa_decrypted.txt
```
![Decrypted File](decrypted_file.png)

---

## Result
- A 2048-bit RSA key pair was successfully generated
- The plaintext file was successfully encrypted using the public key
- The encrypted file was successfully decrypted using the private key
- This demonstrates that **different keys are used for encryption and decryption**

---

## Key Concepts
- **RSA-2048** — RSA algorithm with 2048-bit key length
- **Public Key** — Used to encrypt data, can be shared openly
- **Private Key** — Used to decrypt data, must be kept secret
- **Key Pair** — Public and private keys are mathematically linked

---

## Author
**Temitope Alausa**
GitHub: [TemmyNetGuard](https://github.com/TemmyNetGuard)
