
# Bandit Level 0 → Level 1

## 🎯 Goal
Log into the Bandit server using SSH.  
Find the password for the next level, which is stored in a file called `readme` in the home directory.

---

## 🛠️ Commands Used and What They Do

- `ssh`: Secure Shell — connects you securely to a remote server.
- `ls`: Lists files and directories in the current directory.
- `cat`: Outputs the content of a file to the terminal.

---

## 💻 Steps Taken

1. **Connect to the Bandit Level 0 server using SSH:**  
   ```bash
   ssh bandit0@bandit.labs.overthewire.org -p 2220

2. **Enter the password for Level 0:**
   ```bash
   bandit0
3. **List files in the home directory to find the readme file:**
     ```bash
   ls
**ls** shows that the file readme exists.
     
4. **View the contents of the readme file to get the password for the next level:**
   ```bash
   cat readme
**cat** outputs the text inside the file, which is the password for Level 1.  

5. **Copy the password that appears:**
   
This password will be used to log into Level 1.

**Moving forward, I won't explain logging into each level, or go over commands I have already covered (ls, cat). Make sure to save the passwords for each level somewhere safe so you can easily return to them.**

   
