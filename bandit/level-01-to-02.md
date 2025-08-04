
# Bandit Level 1 → Level 2

## 🎯 Goal
Read the contents of a file named `-` in the home directory to find the next password.


---

## 🛠️ Commands Used and What They Do

- `cat`: Outputs the content of a file to the terminal. However, the file is named `-`, which confuses cat because it typically reads input from the keyboard (stdin). 
So for this level you have to use `cat ./-`, this reads the file named `-` by specifying the path explicitly.


---

## 💻 Steps Taken

1. ** Once logged in, list files in the home directory to find the `-` file:**
     ```bash
   ls
**ls** shows that the file  exists.
     
4. **View the contents of the readme file to get the password for the next level:**
   ```bash
   cat ./-
**cat** outputs the text inside the file, which is the password for Level 2.  

5. **Copy the password that appears:**
   ```bash
  263JGJPfgU6LtdEvgfWU1XP5yac29mFx

This password will be used to log into Level 2. Remember to save it.
