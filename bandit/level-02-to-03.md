
# Bandit Level 2 → Level 3

## 🎯 Goal
Find the password for the next level, which is stored in a file called `--spaces in this filename--`.


---

## 🛠️ Commands Used and What They Do

- `ls`

- `cat`: Again, for this level, we use cat to read the file. However, when a file contains spaces, wrap it in quotes so that the terminal reads it as a single argument.
         Or, alternatively, you could use backslashes to escape the spaces. in the filename 



---

## 💻 Steps Taken

1. ** Once logged in, list files in the home directory to find the `--Spaces in this filename--` file:**
     ```bash
   ls
**ls** shows that the file  exists.
     
4. **View the contents of the file to get the password for the next level:**
   ```bash
   cat ./--spaces\ in\ this\ filename\
   
**cat** outputs the text inside the file, which is the password for Level 3.  

5. **Copy the password that appears:**
   ```bash
   MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx

This password will be used to log into Level 3. Remember to save it.

