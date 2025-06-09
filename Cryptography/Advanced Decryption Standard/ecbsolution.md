
# 🔐 Advanced Decryption Standard - AES-ECB Challenge

**Challenge Title**: Advanced Decryption Standard  
**Points**: 1  
**Flag Format**: `SK-CERT{...}`  
**Encryption Type**: AES (Electronic Codebook Mode - ECB)  
**Key**: `00000000000000000000000000000000` (Hex format, 128-bit all zero)  
**Tool Used**: [CyberChef](https://gchq.github.io/CyberChef/)

---

## 🧠 Challenge Description

> You know that feeling—waking up after a wild night of gambling, pockets full of keys you’re sure are yours, but somehow every single one feels wrong?  
>
> Now imagine being a novice cryptographer after that same night. You’ve got the keys—sure—but absolutely no clue what they open, how they work, or why you even have them in the first place. Welcome to the hangover of cryptography.

We’re given an encrypted file suspected to use **AES encryption in ECB mode**, and a known 128-bit key in hex format. Our goal is to decrypt the file and recover the flag.


## ✅ Decryption Steps Using CyberChef

### 1. 🔓 Load the Encrypted File
- Open [CyberChef](https://gchq.github.io/CyberChef/).
- Upload the encrypted file ecb.dat



### 2. 🔐 Configure AES Decryption
- Add the operation: `AES Decrypt`
- Set the following parameters:

| Parameter      | Value                                   |
|----------------|-----------------------------------------|
| Mode           | ECB                                     |
| Key            | `00000000000000000000000000000000`      |
| Key format     | Hex                                     |
| IV             |                      |
| Input type     | Raw                                     |

### 3. 📤 View the Output
- If correctly decrypted, you’ll see output in the format:


Flag: `SK-CERT{f1r57_15_3cb}`