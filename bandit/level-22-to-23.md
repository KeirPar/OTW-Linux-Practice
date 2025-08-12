# Bandit Level 22 → Level 23
## Goal
A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

## Commands Used and What They Do
- `ls`: Lists files and directories.
- `cat`: Displays the contents of a file.
- `md5sum`: Calculates MD5 hash of input.
- `echo`: Outputs text.
---
## Steps Taken
1. **Look at the cron jobs directory:**
   ```bash
   ls /etc/cron.d/
   ```

2. **Examine the cron job for bandit23:**
   ```bash
   cat /etc/cron.d/cronjob_bandit23
   ```

3. **The cron job shows:**
   ```
   @reboot bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
   * * * * * bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
   ```

4. **Look at the script being executed:**
   ```bash
   cat /usr/bin/cronjob_bandit23.sh
   ```

5. **The script should contain something like:**
   ```bash
   #!/bin/bash
   
   myname=$(whoami)
   mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)
   
   echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"
   
   cat /etc/bandit_pass/$myname > /tmp/$mytarget
   ```

6. **Understand what the script does - it creates a filename based on the username. Since it runs as bandit23, calculate the target filename:**
   ```bash
   echo I am user bandit23 | md5sum | cut -d ' ' -f 1
   ```

7. **This should output a hash like:**
   ```
   8ca319486bfbbc3663ea0fbe81326349
   ```

8. **Read the file with that hash as the filename:**
   ```bash
   cat /tmp/8ca319486bfbbc3663ea0fbe81326349
   ```

9. **Copy the password that appears:**
   ```
   QYw0Y2aiA672PsMmh9puTQuhoz8SyR2G
   ```

This password will be used to log into Level 23. Remember to save it.

---
## Understanding Dynamic File Naming
**Key concepts:**
- **Dynamic filenames**: Scripts can generate filenames based on variables or calculations
- **MD5 hashing**: Creates a fixed-length hash from input text, often used for filename generation
- **Command substitution**: `$(command)` executes the command and uses its output
- **whoami command**: Returns the current username
- **Security through obscurity**: Using hashed filenames to "hide" files (not truly secure)
- **Predictable patterns**: If you understand the algorithm, you can predict the filename
