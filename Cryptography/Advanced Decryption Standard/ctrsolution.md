# 🔐 AES-CTR Decryption Challenge – CyberChef Walkthrough

**Challenge Title**: Advanced Decryption Standard – Easy Like Counting Up to Three  
**Points**: 1  
**Flag Format**: `SK-CERT{...}`  
**Encryption Type**: AES (Advanced Encryption Standard)  
**Mode**: CTR (Counter)  
**Key (Hex)**: `11111111111111111111111111111111`  
**IV/Counter (Hex)**: `99999999999999999999999999999999`  
**Tool Used**: [CyberChef](https://gchq.github.io/CyberChef/)

---

## 🧠 Challenge Description

> The math of this is beyond your comprehension, but you just know this file contains a third flag, encrypted using AES with CTR (counter) mode.

CTR mode turns AES into a stream cipher by encrypting counters and XORing them with plaintext, making it different from ECB or CBC.

---

## 🛠️ Tools Required

- [CyberChef](https://gchq.github.io/CyberChef/) – For decryption.

---

## ✅ Step-by-Step Decryption Guide Using CyberChef

### 1. 📥 Load the Encrypted File
- Open [CyberChef](https://gchq.github.io/CyberChef/).
- Pupload the encrypted data into the **Input** panel.

### 2. 🔐 AES Decrypt (CTR Mode) Configuration
- Add the `AES Decrypt` operation.
- Set the following parameters:

| Parameter   | Value                                      |
|-------------|--------------------------------------------|
| Mode        | CTR                                        |
| Key         | `11111111111111111111111111111111`         |
| Key Format  | Hex                                        |
|IV                    | `99999999999999999999999999999999`         |
| IV Format | Hex                                     |
| Input Type  | Raw                                        |




Flag: `SK-CERT{4nd_7h3_l457_15_c7r}`