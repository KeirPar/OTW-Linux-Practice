# Bandit Level 9 → Level 10
## Goal
The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several '=' characters.

## Commands Used and What They Do
- `strings`: Extracts human-readable text from binary files.
- `grep`: Searches for specific patterns in text.
- `grep "="`: Searches for lines containing the equals sign.
---
## Steps Taken
1. **Look at the data.txt file to see its contents:**
   ```bash
   file data.txt
   ```
   You'll see it's a binary data file, not plain text.

2. **Extract human-readable strings from the binary file:**
   ```bash
   strings data.txt
   ```
   This will show many lines of readable text mixed with gibberish.

3. **Filter the strings to find lines with '=' characters:**
   ```bash
   strings data.txt | grep "="
   ```

4. **Look through the output for lines with multiple '=' characters:**
   ```
   ========== the*2i"4
   =2""L(
   ========== password
   z)========== is
   &========== G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s
   ```

5. **Copy the password that appears after the equals signs:**
   ```
   G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s
   ```

This password will be used to log into Level 10. Remember to save it.

---
## Understanding Binary vs Text Files
**Why we need the `strings` command:**
- Binary files contain both human-readable text and non-printable binary data
- Using `cat` on a binary file will display garbage characters and may mess up your terminal
- `strings` extracts only the printable ASCII characters from binary files
- This is useful for finding hidden text, passwords, or configuration data embedded in binary files
