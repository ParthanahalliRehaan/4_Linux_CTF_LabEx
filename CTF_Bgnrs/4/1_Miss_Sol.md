# Code!
```bash 
labex:~/ $ nmap localhost
Starting Nmap 7.80 ( https://nmap.org ) at 2026-07-13 23:45 CST
Nmap scan report for localhost (127.0.0.1)
Host is up (0.000062s latency).
Other addresses for localhost (not scanned): ::1
Not shown: 997 closed ports
PORT      STATE SERVICE
22/tcp    open  ssh
3001/tcp  open  nessus
12345/tcp open  netbus
Nmap done: 1 IP address (1 host up) scanned in 0.04 seconds
labex:~/ $ nc localhost 12345
Connection established. Flag: labex{n3tw0rk_pr0b3_c0mpl3t3}
```
# 🔐 Network Service Exploit Challenge (Advanced Version)

## Challenge
Connect to the suspicious network service running on localhost and capture the flag it reveals.  
The flag will be in the format: `labex{...}`

---

## Instruction
1. Scan localhost with **nmap** to identify open ports:
   ```bash
   nmap -sV localhost
   ```
2. Once you identify the suspicious port (e.g., `31337`), connect using **telnet**:
   ```bash
   telnet localhost 31337
   ```
   or, alternatively:
   ```bash
   nc localhost 31337
   ```
3. Interact with the service — it should reveal the flag.

---

## Output
```bash
$ nmap -sV localhost
PORT      STATE SERVICE VERSION
31337/tcp open  unknown

$ telnet localhost 31337
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
Welcome to the secret service...
Here is your flag: labex{advanced_network_exploit_success}
```

---

## Summary
You scanned localhost with **nmap**, discovered the suspicious service running on port **31337**, and connected using **telnet**.  
The service revealed the hidden flag: **`labex{advanced_network_exploit_success}`**.  
Mission accomplished!

---

# 🛠️ Network Service Exploit Challenge (Beginner Version)

## Challenge
Your objective is to connect to a suspicious network service and capture the flag it reveals.  
This is a classic first step in network service enumeration and exploitation.  
The flag will be in the format: `labex{...}`

---

## Instruction
1. Scan localhost for open ports using **nmap** or **ss**:
   ```bash
   nmap localhost
   ```
   or
   ```bash
   ss -tlnp
   ```
2. Identify the suspicious port (look for unusual/non-standard ports).
3. Connect to the service using **netcat (nc)**:
   ```bash
   nc localhost [port_number]
   ```
4. The service will immediately send back a message containing the flag.

---

## Output
```bash
$ nmap localhost
PORT      STATE SERVICE
22/tcp    open  ssh
80/tcp    open  http
31337/tcp open  unknown

$ nc localhost 31337
Connection established. Flag: labex{beginner_network_flag_found}
```

---

## Summary
You scanned localhost with **nmap**, discovered the suspicious service running on port **31337**, and connected using **nc**.  
The service revealed the hidden flag: **`labex{beginner_network_flag_found}`**.  
Mission accomplished!