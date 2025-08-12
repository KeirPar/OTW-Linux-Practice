# Bandit Level 15 → Level 16
## Goal
The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL encryption.

## Commands Used and What They Do
- `cat`: Displays the contents of a file.
- `openssl s_client`: OpenSSL command line tool for SSL/TLS connections.
- `ncat --ssl`: Netcat with SSL support.
---
## Steps Taken
1. **Get the current level's password:**
   ```bash
   cat /etc/bandit_pass/bandit15
   ```
   This shows: `jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt`

2. **Connect to localhost port 30001 using SSL with openssl:**
   ```bash
   openssl s_client -connect localhost:30001
   ```

3. **Alternatively, you can use ncat with SSL:**
   ```bash
   ncat --ssl localhost 30001
   ```

4. **After the SSL connection is established, type the current password:**
   ```
   jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt
   ```

4. **The server should respond with:**
   ```
   Correct!
   JQttfApK4SeyHwDlI9SXGR50qclOAil1
   ```

5. **Copy the password:**
   ```
   JQttfApK4SeyHwDlI9SXGR50qclOAil1
   ```

This password will be used to log into Level 16. Remember to save it.

---
## Understanding SSL/TLS Encryption
**Key concepts:**
- **SSL/TLS**: Protocols that provide encrypted communication over networks
- **SSL handshake**: Initial negotiation between client and server to establish encryption
- **openssl s_client**: Command-line tool for testing SSL connections and certificates
- **Port 30001 vs 30000**: Same service concept, but this one requires encrypted communication
- **Certificate warnings**: You may see certificate verification errors - this is normal for self-signed certificates in testing environments
- SSL ensures data transmitted between client and server cannot be intercepted or read by third parties
