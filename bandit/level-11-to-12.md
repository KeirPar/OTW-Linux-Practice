# Bandit Level 11 → Level 12
## Goal
The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions.

## Commands Used and What They Do
- `cat`: Displays the contents of a file.
- `tr`: Translates or transforms characters.
- `tr 'A-Za-z' 'N-ZA-Mn-za-m'`: Applies ROT13 cipher transformation.
---
## Steps Taken
1. **Look at the contents of data.txt:**
   ```bash
   cat data.txt
   ```
   You'll see text that appears to be encoded with ROT13.

2. **Apply ROT13 decoding using the tr command:**
   ```bash
   cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
   ```

3. **The output should show:**
   ```
   The password is 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu
   ```

4. **Copy the password:**
   ```
   5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu
   ```

This password will be used to log into Level 12. Remember to save it.

---
## Understanding ROT13
**What ROT13 is:**
- ROT13 is a simple letter substitution cipher that replaces each letter with the letter 13 positions ahead in the alphabet
- Since the English alphabet has 26 letters, applying ROT13 twice returns the original text (13 + 13 = 26)
- In the `tr` command: 'A-Za-z' represents the input range and 'N-ZA-Mn-za-m' represents the output mapping
- A→N, B→O, C→P... and N→A, O→B, P→C (wrapping around the alphabet)
