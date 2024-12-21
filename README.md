# Here's a LIBC  

This repository contains an exploit script for the **"Here's a LIBC"** challenge from picoCTF 2021. The challenge involves exploiting a binary using the **ret2libc** technique to achieve code execution.  

---

## 🧩 Challenge Overview  

- **Challenge Name**: Here's a LIBC  
- **CTF Event**: picoCTF 2021  
- **Category**: Binary Exploitation  
- **Difficulty**: Hard  

### Challenge Description  
The challenge provides a vulnerable binary and a specific version of `libc.so.6`. The goal is to leverage a **buffer overflow** to execute a **return-to-libc** attack, ultimately executing `/bin/sh` to retrieve the flag.

---

## 📂 Repository Contents  

- `exploit.py` - Python script implementing the ret2libc exploit.  
- `vuln` - The vulnerable binary provided by the challenge.  
- `libc.so.6` - The libc version used for exploitation.  

---

## 🛠️ Technical Details  

### Binary Protections  
The binary is minimally protected, making it a great candidate for exploitation:  
- **Stack Canary**: Disabled  
- **NX**: Enabled  
- **PIE**: Disabled  

### Exploitation Steps  
1. Leak the address of a libc function (e.g., `puts`) to calculate the libc base address.  
2. Compute the addresses of `system`, `/bin/sh`, and `exit` in libc.  
3. Craft a payload to overwrite the return address and redirect execution to `system` with `/bin/sh` as the argument.  

---

## ▶️ How to Run the Exploit  

### Requirements  
- Python 3.x  
- `pwntools` library (`pip install pwntools`)  
- A Linux environment for testing the binary.  

### Instructions  
1. Clone the repository:  
   ```bash
   git clone https://github.com/yourusername/heres-a-libc.git
   cd Heres-a-LIBC
   ```
2. Make the binary executable:
   ```bash
   chmod +x vuln
   ```
3. Run the exploit:
   ```bash
   python3 exploit.py {local|remote}
   ```

## 📜 Disclaimer
**This repository is for educational purposes only. Unauthorized testing or exploitation of systems is illegal and unethical.**

## 📚 Resources
* [picoCTF Official Website](https://picoctf.org/)
* [Pwntools Documentation](https://docs.pwntools.com/en/stable/)
* [Return-to-libc Technique Explained]()
