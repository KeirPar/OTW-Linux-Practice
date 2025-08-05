# Bandit Level 8 → Level 9
## Goal
The password for the next level is stored in the file data.txt and is the only line of text that occurs only once.

## Commands Used and What They Do
- `sort`: Sorts lines of text in a file.
- `uniq`: Reports or omits repeated lines.
- `uniq -u`: Shows only unique lines (lines that appear exactly once).
---
## Steps Taken
1. **Look at the data.txt file to understand its structure:**
   ```bash
   head data.txt
   ```
   You'll see many repeated lines of text.

2. **Sort the file and find lines that appear only once:**
   ```bash
   sort data.txt | uniq -u
   ```

3. **The output should show the unique line:**
   ```
   EN632PlfYiZbn3PhVK3XOGSlNInNE00t
   ```

4. **Copy the password that appears:**
   ```
   EN632PlfYiZbn3PhVK3XOGSlNInNE00t
   ```

This password will be used to log into Level 9. Remember to save it.

---
## Understanding Pipes
**What the | (pipe) does:**
```bash
sort data.txt | uniq -u
```
**How piping works:**
- The `|` symbol takes the output from the left command and sends it as input to the right command
- `sort data.txt` outputs all lines in alphabetical order
- This sorted output is then fed directly into `uniq -u`
- `uniq -u` can only detect duplicates when identical lines are adjacent, which is why sorting first is essential
- The pipe allows you to chain commands together efficiently without creating temporary files
