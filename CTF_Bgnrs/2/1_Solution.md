# 🛡️ Open Port Discovery Mission – Detailed Walkthrough

---

## Step 0: Why 127.0.0.1?
- **127.0.0.1 = Localhost**
  - Always points back to your own machine.
  - In LabEx beginner CTFs, the challenge services run locally inside your sandbox.
- **Why I selected it:**
  - Your Nmap output showed `127.0.0.1` as the scanned target.
  - That’s the default in beginner labs — safe, isolated, no internet scanning.
- **Should you use it in all CTFs?**
  - ✅ Use `127.0.0.1` when the lab explicitly says the target is localhost (like LabEx beginner challenges).
  - ❌ In other CTFs, the target may be a remote IP/hostname given in the instructions (e.g., `10.10.10.5` or `ctf.example.com`). Always follow the challenge setup.

---

## Step 1: Enumerate Ports (Nmap)
- **Purpose:** Discover open ports and services.
- **Command:**
```bash
nmap -p- -sV 127.0.0.1
```
- **Result (your scan):**
  - 22/tcp → SSH
  - 3001/tcp → Nessus
  - 8000/tcp → HTTP-alt

---

## Step 2: Probe Suspicious Ports

### 🔹 Advanced Approach (Netcat)
```bash
# Connect to Nessus port
nc 127.0.0.1 3001

# Connect to HTTP-alt port
nc 127.0.0.1 8000
```
- **Interaction:** Type commands like:
```
help
flag
secret
```

### 🔹 Beginner Approach (Telnet / Curl)
```bash
# Connect to Nessus port
telnet 127.0.0.1 3001

# Fetch HTTP response from port 8000
curl http://127.0.0.1:8000
```
- **Interaction:**  
  - In telnet: type `help`, `flag`, etc.  
  - In curl/browser: check HTML, headers, or hidden endpoints.

---

## Step 3: Retrieve the Flag
- **Expected Output:**
```
FLAG{hidden_service_port_discovery}
```
- The flag will appear in one of the unusual services (likely port 3001 or 8000).

---

## Step 4: Document Findings
- Record:
  - Port number used
  - Service type
  - Commands run
  - Final flag

---

## 🔑 Comparison Table

| Step        | Advanced (nc) | Beginner (telnet/curl) |
|-------------|---------------|-------------------------|
| Discovery   | `nmap`        | `nmap`                 |
| Interaction | `nc` raw socket | `telnet` or `curl`   |
| Ease        | Flexible, powerful | Simple, beginner-friendly |
| Best for    | Custom TCP services | Web/text services |

---

## ✅ Recommended Workflow for LabEx Beginner CTF
1. Run `nmap -p- -sV 127.0.0.1`  
2. Probe port **8000** with `curl http://127.0.0.1:8000`  
3. Probe port **3001** with `telnet 127.0.0.1 3001`  
4. Look for the flag in responses.  
5. Save it in the format `FLAG{...}`.
# Code
```bash
labex:project/ $ nmap 127.0.0.1
Starting Nmap 7.80 ( https://nmap.org ) at 2026-07-08 23:05 CST
Nmap scan report for localhost (127.0.0.1)
Host is up (0.000059s latency).
Not shown: 997 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
3001/tcp open  nessus
8000/tcp open  http-alt

Nmap done: 1 IP address (1 host up) scanned in 0.03 seconds
labex:project/ $ nc 127.0.0.1 3001
help
flag
secret
labex:project/ $ curl http://127.0.0.1:8000
Service is running. Nothing to see here.                                                                                                                              
labex:project/ $ telnet 127.0.0.1 3001
Trying 127.0.0.1...
Connected to 127.0.0.1.
Escape character is '^]'.
help
flag
secret
Connection closed by foreign host.
labex:project/ $ curl http://127.0.0.1:8000/flag
FLAG{d1sc0v3ry_m4st3r_p0rt_8000}                                                                                                       
labex:project/ $ 
```
# Solution by LabEx
# 🧩 Open Port Discovery Challenge (Beginner Version)

## 🎯 Mission
Investigate the local machine (**localhost**) for suspicious open ports.  
Once you find one, interact with the service running on it to retrieve a hidden flag.

---

## 📝 Tasks
1. Use **nmap** to scan localhost for open **TCP ports**.  
   - TCP = Transmission Control Protocol, the standard for reliable communication between computers.  
   - Ports are numbered “doors” into services (e.g., 22 for SSH, 80 for HTTP).  
2. Identify the **unusual, non-standard port** from the scan results.  
   - Standard ports: 22 (SSH), 80 (HTTP), 443 (HTTPS).  
   - Unusual ports are often where flags hide.  
3. Use **curl** to interact with the service running on that port.  
4. Access the `/flag` endpoint to retrieve the flag.

---

## 📌 Requirements
- Must use `nmap` for the port scan.  
- Must use `curl` to interact with the service.  
- The flag is located at the `/flag` path.  
- Output should reveal the flag in the format:
  ```
  FLAG{xxxx}
  ```

---

## 💡 Example Workflow
```bash
# Step 1: Scan localhost for TCP ports
nmap localhost

# Step 2: Identify unusual port (e.g., 9000)

# Step 3: Interact with the service
curl http://localhost:9000

# Step 4: Access the flag endpoint
curl http://localhost:9000/flag
```

---

## 🔎 Hints
- Use `man nmap` to check the manual if needed.  
- A basic scan is often enough.  
- If the main page doesn’t show the flag, remember to check `/flag`.  

---

## ✅ Expected Output
```
FLAG{xxxx}
```
