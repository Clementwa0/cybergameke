## 🔐 Cipher Type: **Atbash Cipher**

### ❓ What is Atbash?

Atbash is one of the oldest known ciphers, dating back to biblical times. It simply replaces each letter of the alphabet with its opposite:

| A ↔ Z | B ↔ Y | C ↔ X | D ↔ W | E ↔ V | F ↔ U | G ↔ T |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| H ↔ S | I ↔ R | J ↔ Q | K ↔ P | L ↔ O | M ↔ N | N ↔ M |
| O ↔ L | P ↔ K | Q ↔ J | R ↔ I | S ↔ H | T ↔ G | U ↔ F |
| V ↔ E | W ↔ D | X ↔ C | Y ↔ B | Z ↔ A |       |       |

So, for example:

* `X` becomes `C`
* `L` becomes `O`
* `I` becomes `R`
* `F` becomes `U`

Thus, **"XLIF" → "CROP"**, which is readable as "DROP" in context.

---

## 🧠 How I Recognized It

The clues were:

1. It’s called **"Almost Classic"** – a hint it's a **classic cipher**.
2. The ciphertext looks like gibberish **but has proper grammar, spaces, and punctuation**. That's typical in **monoalphabetic substitution ciphers** like Atbash or Caesar.
3. Words like `GSV`, `ZYLFG`, and `ULI` appeared repeatedly. In Atbash:

   * `GSV` → `THE`
   * `ZYLFG` → `ABOUT`
   * `ULI` → `FOR`

---

## 🔧 Decryption Steps in CyberChef

You can try it yourself in [CyberChef](https://gchq.github.io/CyberChef/):

1. **Paste the ciphertext** into the Input.
2. Add the **"Atbash Cipher"** operation.
3. The output immediately gives you a readable English conversation and the flag.

---

## 🏁 Flag
SK-CERT{have_you_ever_heard_about_a_black_clock???}





