Here's a **cleaned-up and improved version** of your `README.md`, along with **explanations for each step**.

---

## 🔓 Base64 Repeated Decoding Walkthrough

This short guide shows two ways to decode a deeply nested Base64-encoded message until you reach the final flag. The decoding is repeated multiple times, as the message has been Base64-encoded in several layers.

---

### 🔧 1. Using CyberChef (Graphical Tool)

**Step-by-step:**

1. Go to [CyberChef](https://gchq.github.io/CyberChef/)
2. In the **"Recipe"** panel, add multiple instances of the `From Base64` operation. Start with one and click the **"+"** icon repeatedly (you may need 4–5 times based on the number of layers).
3. In the **Input** panel, paste your Base64-encoded string:

   ```
   VGhlIGVuY29kZWQgbWVzc2FnZSBzYWlkIGRHaGxJR1pzWVdjZ2FYTWdhR2xrWkdWdUlHUmxaWEJsY2lCaVdGWnFZVU5DYTFwWFZuZGFXRWxuV1d4b1YyRnRSa1JrTW1ScFYwWmFj...
   ```
4. Decode each layer one by one and reveal the final plaintext message.

📝 **Tip:** Keep decoding until the output stops being Base64. If you see readable text or a flag format (like `SK-CERT{...}`), you're done!

---

### 🖥️ 2. Using Terminal (r2pipe + custom tool example)



```sh
r.emit 'VGhlIGVuY29kZWQgbWVzc2FnZSBzYWlkIGRHaGxJR1pzWVdjZ2FYTWdhR2xrWkdWdUlHUmxaWEJsY2lCaVdGWnFZVU5DYTFwWFZuZGFXRWxuV1d4b1YyRnRSa1JrTW1ScFYwWmFjVmxWVGtOaE1YQllWbTVrWVZkRmJHNVdiWFJyWWpKS1JtSkZhRTVXTTJoeFZGUkJNV0l4WkhGVGJGcGhUV3RhV2xaR1VtRlRiRXB5VGxVeFZWSnNXbEJWYlhoWFl6RldjVnBGT1ZOTk1tZ3pWa1pTU2sxV2JGZGhSRnBWWW14YVlWcFhkRXRqYkZKVlVsUlNUazFyV2taVlZ6VnpWR3hPUjFkdVZscFdWMUV3VmpJeFlWWkZOVWhhUm1Sb1RXeEtNbGRYZEZkak1VNUhWMjVXVjJKVldsTmFWM2hMVkZaRmVWbDZiRkZWVnpnNVEyYzlQUW89Cg==' \
| r.b64 \
| r.csd b64 \
| r.csd b64 \
| r.csd b64 \
| r.csd b64
```

🧠 **Explanation of each part:**

* `r.emit '...'`: Emits the initial Base64-encoded payload.
* `r.b64`: Decodes the first layer of Base64.
* `r.csd b64`: Custom script decode – likely a helper that recursively applies `base64 decode` on each layer.
* Repeating `r.csd b64` continues decoding nested layers until you reach plain text.

---

### ✅ Final Output

After decoding all the layers, you’ll get:

```text
SK-CERT{4li3nZ_3nc0d3_7h0r0ughlY}
```



