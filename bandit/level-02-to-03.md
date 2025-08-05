# Bandit Level 2 → Level 3
## Goal
The password for the next level is stored in a file called "spaces in this filename" located in the home directory.
---
## Commands Used and What They Do
- `ls`: Lists files and directories in the current directory.
- `cat`: Displays the contents of a file.
- `"filename"`: Using quotes to handle filenames with spaces.
- `\ `: Using backslash to escape spaces in filenames.
---
## Steps Taken
1. **Once logged in, list the contents of the current directory:**
   ```bash
   ls
   ```

2. **You should see a file named "spaces in this filename". Read its contents using quotes:**
   ```bash
   cat "spaces in this filename"
   ```

3. **Alternatively, you can escape the spaces with backslashes:**
   ```bash
   cat spaces\ in\ this\ filename
   ```

4. **Copy the password that appears:**
   ```
   aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG
   ```

This password will be used to log into Level 3. Remember to save it.
