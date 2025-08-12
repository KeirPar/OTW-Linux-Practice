# Bandit Level 19 → Level 20
## Goal
To gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit_pass/bandit20).

## Commands Used and What They Do
- `ls -la`: Lists files with detailed permissions information.
- `./bandit20-do`: Executes the setuid binary.
- `cat`: Displays the contents of a file.
---
## Steps Taken
1. **List the files in the home directory with detailed permissions:**
   ```bash
   ls -la
   ```
   You should see a file called `bandit20-do` with special permissions (the `s` bit set).

2. **Execute the setuid binary without arguments to see usage:**
   ```bash
   ./bandit20-do
   ```
   This will show: `Run a command as another user.`

3. **Use the binary to run a command as bandit20:**
   ```bash
   ./bandit20-do cat /etc/bandit_pass/bandit20
   ```

4. **The command will display the password:**
   ```
   VxCazJaVykI6W36BkBU0mJTCM8rR95XT
   ```

5. **Copy the password:**
   ```
   VxCazJaVykI6W36BkBU0mJTCM8rR95XT
   ```

This password will be used to log into Level 20. Remember to save it.

---
## Understanding SUID Binaries
**Key concepts:**
- **SUID (Set User ID)**: Special permission that allows a program to run with the privileges of its owner
- **Permission notation**: The `s` in the owner execute position (e.g., `-rwsr-xr-x`) indicates SUID
- **Security implications**: SUID binaries are common targets for privilege escalation attacks
- **Real-world examples**: Programs like `passwd`, `sudo`, and `ping` often use SUID
- **How it works**: When you run `./bandit20-do`, it executes with bandit20's privileges, not bandit19's
- **Privilege escalation**: This demonstrates how SUID binaries can be used to gain higher privileges
