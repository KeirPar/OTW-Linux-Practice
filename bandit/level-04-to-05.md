# Bandit Level 4 → Level 5
## Goal
The password for the next level is stored in the only human-readable file in the inhere directory.
---
## Commands Used and What They Do
- `ls`: Lists files and directories in the current directory.
- `cd`: Changes directory.
- `file`: Determines the file type of a given file.
- `cat`: Displays the contents of a file.
- `ls -la`: Lists all files with detailed information, including hidden files.
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

3. **List all files in the directory:**
   ```bash
   ls -la
   ```
   **You should see something like:**
   ```
   -file00  -file01  -file02  -file03  -file04  -file05  -file06  -file07  -file08  -file09
   ```

4. **Check the file type of each file to find the human-readable one:**
   ```bash
   file ./*
   ```
   **This will show the file types. Look for "ASCII text" which indicates human-readable content.**

5. **Read the contents of the human-readable file (typically -file07):**
   ```bash
   cat ./-file07
   ```

6. **Copy the password that appears:**
   ```
   lrIWWI6bB37kxfiCQVb6bEJ5MBsV15pj
   ```

This password will be used to log into Level 5. Remember to save it.

---
## Best Method
**The most efficient way to solve this level:**
```bash
find . -type f -exec file {} + | grep "ASCII"
```
**Why this works better:**
- `find . -type f` finds all files in the **current directory**; this is made clear with the period . before the commands
- `-exec file {} +` runs the `file` command on all found files efficiently
- `| grep "ASCII"` filters the output to only show ASCII text files (human-readable)
- This immediately identifies the human-readable file without having to manually check each one
- You can then directly `cat` the identified file
