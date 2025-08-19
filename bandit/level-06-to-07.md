# Bandit Level 6 → Level 7
## Goal
The password for the next level is stored somewhere on the server and has all of the following properties:
- owned by user bandit7
- owned by group bandit6
- 33 bytes in size
---
## Commands Used and What They Do
- `find`: Searches for files and directories based on various criteria.
- `cat`: Displays the contents of a file.
- `2>/dev/null`: Redirects error messages to suppress "Permission denied" errors.
---
## Steps Taken
1. **Search the entire server for a file with the specified properties:**
   ```bash
   find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
   ```

2. **The command should return a single file path:**
   ```
   /var/lib/dpkg/info/bandit7.password
   ```

3. **Read the contents of the found file:**
   ```bash
   cat /var/lib/dpkg/info/bandit7.password
   ```

4. **Copy the password that appears:**
   ```
   z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S
   ```

This password will be used to log into Level 7. Remember to save it.

