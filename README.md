# ⚙️ How It Works
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
