# Bandit Level 13 → Level 14
## Goal
The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don't get the next password, but you get a private SSH key that can be used to log into the next level.
---
## Commands Used and What They Do
- `ls`: Lists files and directories in the current directory.
- `ssh -i`: Uses a specific private key file for SSH authentication.
- `cat`: Displays the contents of a file.
---
## Steps Taken
1. **List the contents of the current directory:**
   ```bash
   ls
   ```
   You should see a file named `sshkey.private`.

2. **Use the private SSH key to log into bandit14:**
   ```bash
   ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220
   ```

3. **Once logged in as bandit14, read the password file:**
   ```bash
   cat /etc/bandit_pass/bandit14
   ```

4. **Copy the password that appears:**
   ```
   fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq
   ```

This password will be used to log into Level 14. Remember to save it.

---
## Understanding SSH Key Authentication
**How SSH keys work:**
- **Private key**: Kept secret, used to prove your identity (like `sshkey.private`)
- **Public key**: Shared with servers, used to verify the private key
- **Key-based authentication**: More secure than passwords, commonly used in production environments
- **The `-i` flag**: Specifies which private key file to use for authentication
- **File permissions**: Private keys should have restricted permissions (usually 600) for security
- SSH keys eliminate the need to enter passwords and provide stronger authentication
