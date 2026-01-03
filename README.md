# n0pass

**n0pass** is a stateless, deterministic password generator distributed as a **single HTML file**.

No accounts.  
No storage.  
No sync.  
No vault.  

If you don’t type your master password, nothing exists.

---

## What You Get

- One file: `n0pass.html`
- Works online or offline
- Generates unique passwords per site
- Supports password rotation
- Stores absolutely nothing
- Safe against casual access on borrowed or unlocked devices

---

## Core Idea

Instead of saving passwords, n0pass **derives** them.

```
place + identity + master password (+ variant) → deterministic password
```

Same inputs always produce the same password.  
Change any input and the output changes completely.

All computation happens **locally in your browser**.

---

## Usage (Online)

1. Open the file hosted on GitHub Pages  
   Example:
   ```
   https://mikaelv33.github.io/n0pass/n0pass.html
   ```

2. Fill in:
   - **Place**
   - **Identity**
   - **Master Password**
   - **Length**
   - **Variant** (optional, default: 1)

3. Click **Create Password**

4. Copy the result and use it

5. Close the tab  
   Nothing is saved.

---

## Usage (Offline)

1. Download `n0pass.html`
2. Open it in any modern browser
3. Use it exactly the same way

No internet connection is required after loading.

---

## Inputs Explained

### Place
Where the password is used.

Examples:
- `Instagram`
- `Gmail`
- `GitHub`

Be consistent. Different strings generate different passwords.

---

### Identity
Account identifier.

Examples:
- `me@gmail.com`
- `@username`
- `personal account`

---

### Master Password
The **only secret you must remember**.

Rules:
- Long
- High entropy
- Never reused anywhere else

If this is weak, everything is weak.

---

### Variant (Password Rotation)

Used when you need to **change a password for the same site and identity**.

- Default value: `1`
- Increase it only when rotating a password

Example:
- Original password → Variant `1`
- Forced password change → Variant `2`

Everything else stays the same.

This allows password rotation **without changing the master password** and without affecting other sites.

---

### Length
Password length.

- Minimum: 8
- Default: 32
- Maximum: 1024

---

## Security Model

### What n0pass protects against
- Password reuse across sites
- Vault exposure when someone unlocks or borrows your device
- Autofill and account list leaks

### What n0pass does NOT protect against
- Malware or keyloggers
- Offline brute-force if the master password is weak
- Forgetting your master password or variant values

There is **no recovery**.

---

## Technical Notes

- Uses SHA-512 via the browser Web Crypto API
- Deterministic by design
- No external network requests after load
- No localStorage, cookies, or IndexedDB
- Font icons embedded directly as a base64 `.otf` font (single-file distribution)
- **Icon Attribution:** Icons are from [Font Awesome](https://fontawesome.com/) and included under their license

This is a **custom cryptographic construction**, not a standardized KDF.

---

## Comparison to Password Managers

| Feature | n0pass | Password Manager |
|------|------|------------------|
| Stored passwords | No | Yes |
| Vault exposure on unlocked device | No | Yes |
| Autofill | No | Yes |
| Password rotation | Yes (Variant) | Yes |
| Recovery | No | Sometimes |

---

## Important Rules for Users

1. Be consistent with input strings
2. Never reuse the master password elsewhere
3. Use only on trusted devices
4. Track Variant values when rotating passwords
5. If the master password is lost, passwords are unrecoverable
6. This tool favors privacy over convenience

---

## License & Disclaimer

Use at your own risk.

No guarantees.  
No liability.  
No recovery.

---

**n0pass**  
Passwords without storage.  
Derive. Rotate. Forget.
