## Introduction to Cryptology

**Cryptology** is the science of securing information using mathematics to ensure:

- **Confidentiality**
    
- **Integrity**
    
- **Authenticity**
    

#### Branches

- **Cryptography:** Designing encryption/decryption methods
    
- **Cryptanalysis:** Breaking or attacking encryption
    

### History of Cryptology

- Ancient Egypt: Hieroglyphs
    
- Roman era: Caesar cipher
    
- 20th century: Enigma machine, Alan Turing (WWII)
    
- Modern era: Core technology of digital security
    

### Importance & Applications

- **Communication security:** Internet traffic protection
    
- **Data storage:** Encrypted files & databases
    
- **Authentication:** Digital signatures & certificates
    
- **Finance:** Online banking & e-commerce
    
- **Government/Military:** Protection of classified data
    

### Fundamental Cryptographic Terms

#### Encryption & Decryption

- **Encryption:** Converts data into unreadable form using algorithm + key
    
- **Decryption:** Converts encrypted data back to original form
    

#### Keys & Key Management

- **Key:** Secret value used in encryption/decryption
    
- **Key Management:** Key generation, storage, distribution, and destruction
    

#### Public & Private Keys

- **Public Key:** Shared openly (asymmetric encryption)
    
- **Private Key:** Kept secret by owner
    

#### Algorithms & Protocols

- **Algorithms:** AES, RSA, DES
    
- **Protocols:** SSL/TLS, SSH, IPsec
    

### One-Line Summary

> Cryptology secures digital information through encryption techniques, keys, algorithms, and protocols.

---

## Cryptography vs Cryptanalysis — Keypoints

### Cryptography (DEFENSE)

- Goal: **Protect information**
    
- Focus: **Encryption design**
    
- Used by: **System designers, security engineers**
    
- Tools: **Algorithms + keys + protocols**
    
- Outcome: **Confidential, intact, authenticated data**
    

#### 4 Core Goals (CIA + N)

- **Confidentiality** → Only authorized users read data
    
- **Integrity** → Data cannot be altered secretly
    
- **Authentication** → Verify sender identity
    
- **Non-repudiation** → Sender cannot deny action
    

### Types of Cryptography (Easy to Confuse)

### Symmetric Cryptography

- **Same key** for encryption & decryption
    
- Fast, efficient
    
- Key distribution is the main weakness
    

#### Asymmetric Cryptography

- **Public key encrypts, private key decrypts**
    
- Slower than symmetric
    
- Solves key-sharing problem
    

**Memory trick:**

> Symmetric = Same key  
> Asymmetric = A pair of keys

### Cryptanalysis (OFFENSE)

- Goal: **Break encryption without authorization**
    
- Focus: **Finding weaknesses**
    
- Used by: **Attackers, researchers, auditors**
    
- Outcome: **Recovered plaintext or key**
    

### Types of Cryptanalysis (Exam-Tricky)

#### Breaking Attacks

- Directly target **key or ciphertext**
    
- Example: brute forcing keys
    

#### Analysis Attacks

- Target **algorithm or protocol design**
    
- Exploit implementation flaws
    

**Memory trick:**

> Breaking = attack data  
> Analysis = attack design

### Cryptography vs Cryptanalysis (Must-remember table logic)

- **Purpose:** Protect vs Break
    
- **Mindset:** Defensive vs Offensive
    
- **Methods:** Algorithms vs Weakness exploitation
    
- **Relationship:** Opposites but complementary
    

### Fundamental Principles (Very Important)

#### Kerckhoffs’s Principle

- **Algorithm can be public**
    
- **Security must rely on key secrecy**
    

Memory trick:

> “Hide the key, not the math”

#### Shannon’s Uncertainty Theory

- Ciphertext should look **random**
    
- No visible patterns or statistics
    

Memory trick:

> “Good encryption looks like noise”

### Cryptanalysis Techniques (High-yield)

#### Brute Force

- Tries **all possible keys**
    
- Feasible if key size is small
    

#### Dictionary Attack

- Tries **common words/passwords**
    
- Faster than brute force
    

#### Side-Channel Attack

- Uses **time, power, heat, sound**
    
- Attacks the **implementation**, not math
    

#### Statistical Attack

- Uses **patterns & frequency**
    
- Common in weak ciphers
    

Memory ladder:

> Dictionary → Brute → Statistical → Side-Channel (physical)

### Why Both Are Important

- Cryptography → **Builds security**
    
- Cryptanalysis → **Tests security**
    
- Weakness discovery → **Stronger future algorithms**
    

Final memory line:

> Cryptography locks the door, cryptanalysis tests whether it actually holds.


---

## Symmetric Encryption — Keypoints

### Core Concept

- **Same key** used for **encryption + decryption**
    
- Sender & receiver **share one secret**
    
- **Fast**, but **key sharing is the main weakness**
    

Memory hook:

> “One key, both sides”

### Algorithm Types (Very Important)

#### 1️⃣ Block Ciphers

- Encrypt data in **fixed-size blocks**
    
- Require **modes of operation**
    

##### DES

- **56-bit key**
    
- **Broken / obsolete**
    
- Weak against brute force
    

##### 3DES

- DES applied **3 times (E-D-E)**
    
- **168-bit key**
    
- More secure than DES, but **slow**
    

##### AES (Most Important)

- Keys: **128 / 192 / 256 bits**
    
- **Fast + secure**
    
- Industry standard
    

Memory ladder:

> DES ❌ → 3DES ⚠️ → AES ✅

#### 2️⃣ Stream Ciphers

- Encrypt data **bit-by-bit / byte-by-byte**
    
- Good for **real-time data**
    

##### RC4

- Fast but **cryptographically broken**
    
- No longer recommended
    

##### Salsa20 / ChaCha20

- Modern & secure
    
- Designed for **low-power devices**
    
- Common in **mobile & IoT**
    

Memory hook:

> RC4 = old & weak  
> ChaCha = modern & strong

### Advantages (Why Symmetric is Used)

- **Very fast**
    
- **Low CPU usage**
    
- Simple implementation
    

Exam phrase:

> “Performance over convenience”

### Disadvantages (Exam Favorite)

- **Key distribution problem**
    
- Hard key management at scale
    
- **Key compromise = total data compromise**
    

One-line killer:

> If the key leaks, everything leaks.

### Block Cipher Modes (HIGH-YIELD)

#### ECB (Electronic Codebook)

- Same plaintext → same ciphertext
    
- **Patterns visible**
    
- ❌ **Never secure**
    

Memory:

> ECB = “Electronic Coloring Book”

#### CBC (Cipher Block Chaining)

- Each block depends on previous block
    
- Uses **IV**
    
- More secure than ECB
    

#### CFB

- Block cipher behaves like **stream cipher**
    
- Uses ciphertext feedback
    

#### OFB

- Stream-like mode
    
- Errors **do not propagate**
    

#### CTR (Counter Mode)

- Uses **counter + key**
    
- **Parallel encryption**
    
- Very fast & scalable
    

Mode ranking (security + usage):

> ECB ❌ → CBC ⚠️ → CTR ✅

### Applications (Real-World)

- **Data storage:** Disk & file encryption
    
- **Communication:** VPN, SSL/TLS (bulk encryption)
    
- **Authentication systems:** Session keys
    

Important insight:

> SSL/TLS uses **asymmetric to share keys**, then **symmetric for data**.

### Final Memory Snapshot

- Same key → symmetric
    
- Fast but key sharing is risky
    
- AES = king
    
- ECB = evil
    
- CTR = modern & fast
    

---

## Asymmetric Encryption — Keywords

### Core Idea

- **Two keys**
    
    - **Public key** → encrypt / verify
        
    - **Private key** → decrypt / sign
        
- **More secure**
    
- **Slower than symmetric**
    

### Algorithms (Just remember WHY)

#### RSA

- 1024 / 2048 / 4096 bits
    
- Encryption + signatures
    
- Based on **prime factorization**
    

#### ECC

- Shorter keys, same security
    
- **256-bit ECC ≈ 2048-bit RSA**
    
- Used in **mobile / IoT**
    

#### ElGamal

- Encryption + signatures
    
- **Discrete logarithm**
    

#### DSA

- **Signatures only**
    
- **Discrete logarithm**
    

### Advantages

- No key-sharing problem
    
- Public key can be shared
    
- Supports **authentication**
    

### Disadvantages

- Slow
    
- High CPU usage
    

### PKI (Public Key Infrastructure)

#### Components

- **CA** → issues & signs certificates
    
- **RA** → verifies identity
    
- **Digital Certificate** → public key + identity
    
- **Certificate Repository** → storage
    

### Digital Signatures (Flow Keywords)

#### Create

- Hash message
    
- Encrypt hash with **private key**
    

#### Verify

- Decrypt with **public key**
    
- Compare hashes
    

### Applications (Exam Keywords)

- **SSL/TLS**
    
- **PGP / S-MIME**
    
- **VPN**
    
- **Digital certificates**
    
- **Authentication**
    

### One-Line Memory Hook

> Asymmetric crypto = trust, identity, and key exchange — not bulk encryption.


---

## Hash Functions — Keywords

### Core Idea

- **Input:** any length
    
- **Output:** fixed length (hash / digest)
    
- **One-way function**
    

### Core Properties (Must remember)

- **Deterministic**
    
- **Fast**
    
- **Avalanche effect**
    
- **Collision resistant**
    
- **Preimage resistant**
    

Memory set:

> Same input → same hash  
> Small change → big hash change

### Uses (Exam Keywords)

- **Data integrity**
    
- **Password storage**
    
- **Digital signatures**
    
- **Certificates**
    
- **Database indexing**
    

### Hash Algorithms (Status-based)

#### MD5

- 128-bit
    
- ❌ **Broken**
    
- Collisions exist
    

#### SHA-1

- 160-bit
    
- ❌ **Broken**
    
- Collision found (2017)
    

#### SHA-2

- SHA-224 / 256 / 384 / 512
    
- **Secure**
    
- Widely used
    

#### SHA-3

- Keccak based
    
- **Secure**
    
- Different design
    

#### RIPEMD-160

- 160-bit
    
- Alternative hash
    

Memory ladder:

> MD5 ❌ → SHA-1 ❌ → SHA-2 ✅ → SHA-3 ✅

### Security Properties (Hard-to-remember)

- **One-way**
    
- **Collision resistance**
    
- **Second preimage resistance**
    
- **Avalanche effect**
    

### Hash Attacks (High-Yield)

- **Collision attack**
    
- **Preimage attack**
    
- **Second preimage attack**
    
- **Rainbow table attack**
    

Memory trick:

> Collision = two inputs  
> Preimage = find input  
> Rainbow = precomputed hashes

### Applications (Keywords Only)

- Password hashing
    
- Digital signatures
    
- SSL/TLS
    
- IPsec
    
- File integrity checks
    

### One-Line Recall

> Hashing ≠ encryption  
> Hashing = integrity & verification

---

## Digital Signatures — Keywords

### Core Idea

- **Asymmetric cryptography**
    
- Verifies **identity + integrity**
    
- Uses **private key (sign)** & **public key (verify)**
    

### Purposes (Must Remember)

- **Authentication**
    
- **Integrity**
    
- **Non-repudiation**
    

Memory set:

> Who sent it ✔  
> Not changed ✔  
> Cannot deny ✔

### Working Principle (Flow Keywords)

#### Signing

- **Hash document**
    
- **Encrypt hash with private key**
    
- → Digital signature
    

#### Verification

- **Hash received document**
    
- **Decrypt signature with public key**
    
- **Compare hashes**
    

One-line flow:

> Hash → Private key → Signature  
> Public key → Compare hash

### Digital Signature Algorithms

#### RSA

- Sign + encrypt
    
- Reliable & common
    

#### DSA

- **Signature only**
    
- Faster sign, slower verify
    

#### ECDSA

- Elliptic Curve
    
- Short keys, high security
    
- Mobile / IoT
    

### Digital Certificates & PKI

#### Digital Certificate

- **Public key + identity**
    
- **X.509 format**
    
- Signed by CA
    

#### CA (Certificate Authority)

- Issues & validates certificates
    

#### CRL

- Revoked certificates list
    

### Applications (Keywords Only)

- **PGP / S-MIME (Email)**
    
- **Electronic contracts**
    
- **Software signing**
    
- **Banking transactions**
    
- **E-gov / E-commerce**
    

### Security Requirements

- Strong asymmetric algorithm
    
- Secure hash (SHA-256 / SHA-3)
    
- Secure **private key storage**
    
- Certificate & CRL management
    

### One-Line Recall

> Digital signature = hash + private key + trust via certificates

---

## Cryptographic Protocols — Keywords

### Core Idea

- Rules + algorithms
    
- Secure **communication**
    
- Ensure **confidentiality, integrity, authentication**
    

### SSL / TLS

- **HTTPS**
    
- Browser ↔ Server
    
- **Handshake**
    
- Session key
    
- Uses:
    
    - Asymmetric (key exchange)
        
    - Symmetric (data)
        
    - Certificates
        
    - Hashing
	

### IPsec

- **Secures IP packets**
    
- Used in **VPNs**
    

### Components

- **ESP** → encryption + integrity
    
- **AH** → integrity + auth
    
- **IKE** → key exchange
    

### SSH

- **Secure remote login**
    
- Server management
    

Flow:

- Handshake
    
- Authentication
    
- Encrypted session
    

### PGP

- **Email security**
    
- Encrypt + Sign
    

Uses:

- Symmetric (message)
    
- Asymmetric (key)
    
- Digital signature
    

### Kerberos

- **Authentication protocol**
    
- Enterprise / AD
    

Keywords:

- **TGS**
    
- Tickets
    
- Session keys
    
- Symmetric crypto
    

### OAuth

- **Authorization (not authentication)**
    
- Third-party access
    

Keywords:

- Authorization code
    
- Access token
    
- HTTPS
    

### Security Depends On

- Strong algorithms (AES, RSA, SHA-256)
    
- Proper key management
    
- Updates & patches
    
- Correct implementation
    

### Applications (One-liners)

- **Web:** TLS
    
- **Network:** IPsec, SSH
    
- **Email:** PGP
    
- **Auth:** Kerberos, OAuth
    
- **Data:** Secure transfer
    

### One-Line Recall

> Protocols define **how crypto is used**, not the crypto itself.

---

Perfect 👍  
Here are **VERY high-level, ultra-compressed, keyword-only notes** for **Cryptanalysis Techniques** — **no extra detail**, just **hard memory anchors**.

## Cryptanalysis Techniques — Keywords

### Core Idea

- **Break encryption**
    
- **Find weaknesses**
    
- Test cryptosystem security
    

### Attack Types (High-Yield)

#### Brute Force

- Try **all keys**
    
- Time ∝ key length
    
- Defense: **long keys**
    

#### Dictionary Attack

- Common passwords
    
- Wordlists
    
- Defense: **strong passwords**
    

#### Side-Channel

- **Power**
    
- **Timing**
    
- **EM leakage**
    
- Attacks implementation
    
- Defense: hardware/software protection
    

#### Known Plaintext

- Plaintext + ciphertext known
    
- Exploits algorithm weakness
    
- Defense: strong algorithms
    

#### Frequency Analysis

- Character/block frequency
    
- Breaks **simple ciphers**
    
- Defense: modern crypto
    

#### Differential Cryptanalysis

- Input difference → output difference
    
- Targets **block ciphers**
    
- Defense: resistant cipher design
    

#### Linear Cryptanalysis

- Linear approximations
    
- Targets cipher structure
    
- Defense: resistant cipher design
    

#### Man-in-the-Middle (MitM)

- Intercept communication
    
- Alters/extracts data
    
- Defense: secure key exchange, E2E encryption
    

### Usage of Cryptanalysis

- **Security testing**
    
- **Digital forensics**
    
- **Military / intelligence**
    
- **Cyber attacks**
    

### One-Line Recall

> Cryptanalysis attacks **keys, algorithms, implementations, or communication channels**.

---

	