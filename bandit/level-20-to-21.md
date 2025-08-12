# Bandit Level 20 → Level 21
## Goal
There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21).

## Commands Used and What They Do
- `ls -la`: Lists files with detailed permissions information.
- `nc -l`: Netcat in listening mode.
- `./suconnect`: The setuid binary that connects to a specified port.
- `&`: Runs a command in the background.
---
## Steps Taken
1. **List the files in the home directory:**
   ```bash
   ls -la
   ```
   You should see a file called `suconnect` with SUID permissions.

2. **Test the binary to understand its usage:**
   ```bash
   ./suconnect
   ```
   This will show: `Usage: ./suconnect <portnumber>`

3. **Set up a netcat listener on a port (e.g., 1234) in the background:**
   ```bash
   echo "VxCazJaVykI6W36BkBU0mJTCM8rR95XT" | nc -l -p 1234 &
   ```

4. **Connect to the listener using the suconnect binary:**
   ```bash
   ./suconnect 1234
   ```

5. **The binary will connect, verify the password, and return the next password:**
   ```
   Read: VxCazJaVykI6W36BkBU0mJTCM8rR95XT
   Password matches, sending next password
   NvEJF7oVjkddltPSrdKEFOllh9V1IBcq
   ```

6. **Copy the password:**
   ```
   NvEJF7oVjkddltPSrdKEFOllh9V1IBcq
   ```

This password will be used to log into Level 21. Remember to save it.

---
## Understanding Client-Server Communication
**Key concepts:**
- **Client-server model**: The `suconnect` binary acts as a client, netcat acts as a server
- **Background processes**: The `&` symbol runs netcat in the background so you can run other commands
- **Port-based communication**: Both client and server must use the same port number
- **Echo and pipe**: `echo "password" | nc -l -p 1234` sends the password when something connects
- **Authentication protocol**: The binary implements a simple challenge-response authentication
- This demonstrates how network services can verify credentials and respond accordingly
