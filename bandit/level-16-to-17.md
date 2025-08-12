# Bandit Level 16 → Level 17
## Goal
The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000. First find out which of these ports have a server listening on them. Then find out which of those speak SSL and which don't. There is only 1 server that will give you the next credentials, and it only speaks SSL.

## Commands Used and What They Do
- `nmap`: Network exploration tool and security scanner.
- `ncat --ssl`: Netcat with SSL support for encrypted connections.
- `openssl s_client`: Alternative tool for SSL connections.
---
## Steps Taken
1. **Scan for open ports in the specified range:**
   ```bash
   nmap -p 31000-32000 localhost
   ```

2. **For better service detection, use the -sV flag:**
   ```bash
   nmap -sV -p 31000-32000 localhost
   ```
   This will show which ports are open and what services are running on them.

2. **The scan should reveal several open ports. Test each one for SSL support:**
   ```bash
   ncat --ssl localhost 31046
   ncat --ssl localhost 31518
   ncat --ssl localhost 31691
   ncat --ssl localhost 31790
   ncat --ssl localhost 31960
   ```

3. **For each SSL-enabled port, submit the current password:**
   ```bash
   cat /etc/bandit_pass/bandit16
   ```
   Copy the password: `JQttfApK4SeyHwDlI9SXGR50qclOAil1`

4. **Test the SSL ports by sending the password. The correct port will return an SSH private key:**
   ```
   -----BEGIN RSA PRIVATE KEY-----
   MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
   ...
   -----END RSA PRIVATE KEY-----
   ```

5. **Save this private key to a file:**
   ```bash
   mkdir /tmp/level16
   cd /tmp/level16
   # Paste the private key into a file using nano text editor
   nano sshkey.private
   # Or alternatively, you can redirect the output directly:
   # ncat --ssl localhost 31790 < /etc/bandit_pass/bandit16 > sshkey.private
   chmod 600 sshkey.private
   ```

6. **Use the private key to log into bandit17:**
   ```bash
   ssh -i sshkey.private bandit17@bandit.labs.overthewire.org -p 2220
   ```

This will log you into Level 17 directly using key-based authentication.

---
## Understanding Port Scanning
**Key concepts:**
- **Port scanning**: Technique to discover open ports and services on a network host
- **nmap**: Industry-standard tool for network discovery and security auditing
- **-sV flag**: Enables service version detection, helping identify what's running on each port
- **Port ranges**: Ports 31000-32000 represent a specific range to scan
- **Service detection**: Not all open ports speak the same protocol (some SSL, some plain text)
- **Security implications**: Port scanning is often the first step in network reconnaissance
- Always ensure you have permission before scanning networks other than your own
