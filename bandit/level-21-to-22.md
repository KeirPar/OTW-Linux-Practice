# Bandit Level 21 → Level 22
## Goal
A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

## Commands Used and What They Do
- `ls`: Lists files and directories.
- `cat`: Displays the contents of a file.
- `crontab`: System for scheduling automated tasks.
---
## Steps Taken
1. **Look in the cron directory for scheduled jobs:**
   ```bash
   ls /etc/cron.d/
   ```
   You should see several cron job files, including ones for different bandit levels.

2. **Examine the cron job for bandit22:**
   ```bash
   cat /etc/cron.d/cronjob_bandit22
   ```

3. **The cron job should show something like:**
   ```
   @reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
   * * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
   ```

4. **Look at the script that's being executed:**
   ```bash
   cat /usr/bin/cronjob_bandit22.sh
   ```

5. **The script should contain:**
   ```bash
   #!/bin/bash
   chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
   cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
   ```

6. **Read the file that the script creates:**
   ```bash
   cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
   ```

7. **Copy the password that appears:**
   ```
   WdDozAdTM2z9DiFEQ2mGlwngMfj4EZff
   ```

This password will be used to log into Level 22. Remember to save it.

---
## Understanding Cron Jobs
**Key concepts:**
- **Cron**: Unix time-based job scheduler for running tasks automatically
- **Cron syntax**: `* * * * *` represents minute, hour, day, month, weekday
- **@reboot**: Special cron directive that runs the command at system startup
- **/etc/cron.d/**: Directory containing system-wide cron job definitions
- **Output redirection**: `&> /dev/null` discards all output (both stdout and stderr)
- **Security implications**: Cron jobs running as privileged users can be exploited if misconfigured
- This level demonstrates how automated tasks can inadvertently expose sensitive information
