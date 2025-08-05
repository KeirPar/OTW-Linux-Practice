# Bandit Level 3 → Level 4
## Goal
The password for the next level is stored in a hidden file in the inhere directory.

## Commands Used and What They Do
- `ls`: Lists files and directories in the current directory.
- `ls -a`: Lists all files, including hidden ones (those starting with a dot .).
- `cd`: Changes directory.
- `cat`: Displays the contents of a file.
---
## Steps Taken
1. **Once logged in, list the contents of the current directory to find inhere:**
   ```bash
   ls
   ```
     
2. **Change into the inhere directory:**
   ```bash
   cd inhere
   ```

3. **List all files in the directory, including hidden ones:**
   ```bash
   ls -a
   ```
   **You should see something like:**
   ```
   .  ..  .hidden
   ```

4. **Read the contents of the hidden file .hidden:**
   ```bash
   cat .hidden
   ```

5. **Copy the password that appears:**
   ```
   2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ
   ```

This password will be used to log into Level 4. Remember to save it.
