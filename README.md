# 🔐 Microsoft Edge Password Extractor (Forensic Educational Tool)
## 📌 Overview

This project is a forensic utility designed for educational and research purposes.
It demonstrates how saved credentials in Microsoft Edge are stored locally on a Windows system and how they can be decrypted using the Windows Data Protection API (DPAPI).

⚠️ **Disclaimer:** This tool is intended only for digital forensic analysis, system recovery, and educational research.
Using it on devices you do not own or have explicit permission for may violate privacy laws and computer misuse acts.

## 🚀 Features

* Extracts saved website logins (URL, username, password) from Microsoft Edge.
* Uses the master key from Edge’s Local State file.
* Decrypts AES-encrypted credentials with DPAPI + AES-GCM.
* Works even if the Edge database is locked (copies it to a temp location).
* Outputs credentials in a clean terminal view (optional CSV/JSON export can be added).

## ⚙️ How It Works
### 1. Locate Master Key
* Microsoft Edge stores an encrypted master key in
```
AppData\Local\Microsoft\Edge\User Data\Local State
```
* The key is encrypted using Windows DPAPI.
* Script decrypts it with win32crypt.

### 2. Extract Passwords Database
* Login data is stored in a SQLite database:
```
AppData\Local\Microsoft\Edge\User Data\Default\Login Data
```
* Script copies this DB to a temp folder to prevent lock errors.

### 3. Decrypt Saved Passwords
* Passwords are encrypted with AES (v10/v11 format).
* Script uses the master key + AES-GCM to decrypt them.

### 4. Display Results
* Shows: URL, Username, Password
* Example:
```
URL: https://github.com
Username: testuser
Password: mySecret123
```

## 📦 Requirements

* Python 3.9+\
* Install dependencies:
```
pip install pycryptodome pypiwin32
```
## ▶️ Usage
Run the script:
```
python edge_forensic.py
```
Sample Output:
```
🔍 Extracting Microsoft Edge Saved Passwords...

========== Saved Edge Passwords ==========

URL: https://example.com
Username: alice
Password: mypassword123
----------------------------------------

✅ Done. All output shown in terminal.
```
## 📂 Project Structure
```
edge_forensic.py   # Main script
README.md          # Documentation
```
## 🔒 Legal & Ethical Notice
This project is provided strictly for educational and forensic purposes:

* ✔️ Cybersecurity research
* ✔️ Incident response / recovery
* ✔️ Digital forensics courses

❌ Do not use this tool on systems or accounts you don’t own or have **explicit permission** to test.
The author(s) take **no responsibility** for misuse.

## 📜 License

Released under the **MIT License** – free to use, modify, and share for ethical purposes.
