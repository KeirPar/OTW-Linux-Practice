# Bandit Level 12 → Level 13
## Goal
The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work using mkdir. Then copy the file using cp, and rename it using mv.

## Note
This level is by far the longest and most difficult level so far. There are many different ways you can go about completing it.  

## Commands Used and What They Do
- `mkdir`: Creates a directory.
- `cp`: Copies files.
- `xxd -r`: Reverses a hexdump back to binary data.
- `file`: Determines file type.
- `gzip -d`: Decompresses gzip files.
- `bzip2 -d`: Decompresses bzip2 files.
- `tar -xf`: Extracts tar archives.
- `mv`: Renames or moves files.
---
## Steps Taken
1. **Create a working directory and copy the file:**
   ```bash
   cd /tmp
   mktemp -d
   cd
   cp data.txt /tmp/tmp.xLdab2iPd2 (example temp directory)
   cd /tmp/tmp.xLdab2iPd2
   mv data.txt hexdump_data 
   ```

2. **Convert the hexdump back to binary:**
   ```bash
   xxd -r hexdump_data compressed
   ```

3. **Check what type of file it is:**
   ```bash
   file binary_file
   ```
   It should show it's a gzip compressed file.

   Or check the top part of the file and see if it has `1f 8b`, which corresponds to a gzip file. Or `425a`, this corresponds to a bzip2 file.

5. **Rename and decompress the gzip file:**
   ```bash
   mv binary_file data.gz
   gzip -d data.gz
   ```

6. **Continue checking file types and decompressing:**
   ```bash
   file data
   ```
   Keep repeating this process, renaming and using the appropriate decompression tool:
   - For gzip: `gzip -d filename.gz`
   - For bzip2: `bzip2 -d filename.bz2` 
   - For tar: `tar -xf filename.tar`

7. **After several iterations of decompression, you'll eventually get:**
   ```bash
   file data8
   cat data8
   ```

8. **The final output should show:**
   ```
   The password is 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL
   ```

9. **Copy the password:**
   ```
   8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL
   ```

This password will be used to log into Level 13. Remember to save it.

---
## Understanding File Types and Compression
**How to identify file types:**
- **Use the `file` command**: This examines the file's "magic bytes" (first few bytes) to identify the actual format
- **Common file signatures**:
  - Gzip files start with `1f 8b` in hex
  - Bzip2 files start with `BZ` (or `42 5a` in hex)
  - Tar files have specific header structures
- **Don't trust file extensions**: A file named `data` could be any format - always check with `file`
- **Magic bytes vs extensions**: The `file` command reads the actual file content, not just the filename

**Key concepts:**
- **Hexdump**: A representation of binary data in hexadecimal format, created with `xxd` or `hexdump`
- **Multiple compression**: Files can be compressed multiple times with different algorithms
- **File signatures**: Each compression format has unique "magic bytes" that `file` command recognizes
- Always use `file` command to identify the actual format before attempting decompression
- Common extensions: `.gz` (gzip), `.bz2` (bzip2), `.tar` (tape archive)
