## AES-CBC Decryption Challenge – CyberChef Walkthrough

**Challenge Title**: Advanced Decryption Standard – CBC Mode  
**Points**: 1  
**Flag Format**: `SK-CERT{...}`  
**Encryption Type**: AES (Advanced Encryption Standard)  
**Mode**: CBC (Cipher Block Chaining)  
**Key (Hex)**: `00000000000000000000000000000000`  
**IV (Hex)**: `01020304050607080102030405060708`  
**Tool Used**: [CyberChef](https://gchq.github.io/CyberChef/)

---

## 🧠 Challenge Description

> You can’t, for the life of you, remember why each flag ended up with a different chaining method. Must’ve been one heck of a night...

This file contains the flag encrypted using **AES in CBC mode** with a known key and IV.


## 🛠️ Tools Required

- [CyberChef](https://gchq.github.io/CyberChef/) For decryption.

## ✅ Step-by-Step Decryption Guide Using CyberChef

### 1. 📥 Load the Encrypted File
- Open [CyberChef](https://gchq.github.io/CyberChef/).
- Upload the encrypted data into the **Input** panel.

### 2. 🔍 Determine Ciphertext Format

> ⚠️ Be sure to detect the encoding first or try both if unsure.

### 3. 🔐 AES Decrypt Configuration
- Add the `AES Decrypt` operation to the recipe.
- Configure as follows:

| Parameter   | Value                                      |
|-------------|-------------------------------------------|
| Mode        | CBC                                        |
| Key         | `00000000000000000000000000000000`         |
| Key Format  | Hex                                        |
| IV          | `01020304050607080102030405060708`         |
| IV Format   | Hex                                        |
| Input Type  | Raw                                        |

📌 CBC mode **requires an IV**, unlike ECB. Both key and IV must match exactly with the encryption values.




Flag: `SK-CERT{cbc_m0d3_15_n3x7}`