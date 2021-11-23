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

## Python 3 Web Server (-python or -python3)

Format for a Python3 web server `sudo python3 -m http.server 80`

## Msfvenom (-msfvenom)

Standard format for msfvenom `msfvenom -p <PAYLOAD> <OPTIONS>`

