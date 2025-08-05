# Bandit Level 1 → Level 2
## Goal
The password for the next level is stored in a file called - located in the home directory.

## Commands Used and What They Do
- `ls`: Lists files and directories in the current directory.
- `cat`: Displays the contents of a file.
- `cat ./-`: Reads a file with a special name like "-" by specifying its path.
---
## Steps Taken
1. **Once logged in, list the contents of the current directory:**
   ```bash
   ls
   ```

2. **You should see a file named - (dash). Try to read it with cat:**
   ```bash
   cat -
   ```
   **This won't work because the shell interprets - as stdin.**

3. **Read the file by specifying its full path:**
   ```bash
   cat ./-
   ```

4. **Copy the password that appears:**
   ```
   rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi
   ```

This password will be used to log into Level 2. Remember to save it.
