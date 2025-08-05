# Bandit Level 7 → Level 8
## Goal
The password for the next level is stored in the file data.txt next to the word "millionth".
---
## Commands Used and What They Do
- `ls`: Lists files and directories in the current directory.
- `cat`: Displays the contents of a file.
- `grep`: Searches for specific patterns or words in text.
---
## Steps Taken
1. **Once logged in, list the contents of the current directory:**
   ```bash
   ls
   ```

2. **You should see a file named data.txt. Check its size (it's quite large):**
   ```bash
   cat data.txt
   ```
   **This will show thousands of lines - not practical to read through manually.**

3. **Use grep to find the line containing "millionth":**
   ```bash
   grep "millionth" data.txt
   ```

4. **The output should show:**
   ```
   millionth	TESKZC0XvTetK0S9xNwm25STk5iWrBvP
   ```

5. **Copy the password that appears:**
   ```
   TESKZC0XvTetK0S9xNwm25STk5iWrBvP
   ```

This password will be used to log into Level 8. Remember to save it.
