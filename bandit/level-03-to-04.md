
# Bandit Level 3 → Level 4

## 🎯 Goal
The password for the next level is stored in a hidden file in the inhere directory.


---

## 🛠️ Commands Used and What They Do

- `ls -a`: Lists all files, including hidden ones (those starting with a dot .).

- `cd`: Changes directory.

- `cat` : Prints file contents.



---

## 💻 Steps Taken

1. ** Once logged in, list files in the home directory to find the `--Spaces in this filename--` file:**
     ```bash
   ls
**ls** shows that the file  exists.
     
4. **View the contents of the file to get the password for the next level:**
   ```bash
   cat ./--spaces\ in\ this\ filename--\
   
**cat** outputs the text inside the file, which is the password for Level 3.  

5. **Copy the password that appears:**
   ```bash
   MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx

This password will be used to log into Level 3. Remember to save it.

