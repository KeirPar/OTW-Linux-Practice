# Bandit Level 12 → Level 13
## Goal
The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work using mkdir. Then copy the file using cp, and rename it using mv.

## Commands Used and What They Do
- `mkdir`: Creates a directory.
- `cp`: Copies files.
- `xxd -r`: Reverses a hexdump back to binary data.
- `file`: Determines file type.
- `gunzip`: Decompresses gzip files.
- `bunzip2`: Decompresses bzip2 files.
- `tar -xf`: Extracts tar archives.
- `mv`: Renames or moves files.
---
## Steps Taken
1. **Create a working directory and copy the file:**
   ```bash
   mkdir /tmp/level12
   cp data.txt /tmp/level12/
   cd /tmp/level12
   ```

2. **Convert the hexdump back to binary:**
   ```bash
   xxd -r data.txt > binary_file
   ```

3. **Check what type of file it is:**
   ```bash
   file binary_file
   ```
   It should show it's a gzip compressed file.

4. **Rename and decompress the gzip file:**
   ```bash
   mv binary_file data.gz
   gunzip data.gz
   ```

5. **Continue checking file types and decompressing:**
   ```bash
   file data
   ```
   Keep repeating this process, renaming and using the appropriate decompression tool:
   - For gzip: `gunzip filename.gz`
   - For bzip2: `bunzip2 filename.bz2` 
   - For tar: `tar -xf filename.tar`

6. **After several iterations of decompression, you'll eventually get:**
   ```bash
   file data8
   cat data8
   ```

7. **The final output should show:**
   ```
   The password is 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL
   ```

8. **Copy the password:**
   ```
   8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL
   ```

This password will be used to log into Level 13. Remember to save it.

---
## Understanding File Compression
**Key concepts:**
- **Hexdump**: A representation of binary data in hexadecimal format, created with `xxd` or `hexdump`
- **Multiple compression**: Files can be compressed multiple times with different algorithms
- **File signatures**: Each compression format has unique "magic bytes" that `file` command recognizes
- Always use `file` command to identify the actual format before attempting decompression
- Common extensions: `.gz` (gzip), `.bz2` (bzip2), `.tar` (tape archive)
