# Code
```bash
labex:project/ $ ls -la
total 4
drwxr-xr-x 1 labex labex    6 Jul 18  2024 .
drwxr-x--- 1 labex labex 4096 Jul  9 11:03 ..
labex:project/ $ sudo find / -name flag.txt 2>/dev/null
/opt/backups/.secret/flag.txt
labex:project/ $ cat /opt/backups/.secret/flag.txt
cat: /opt/backups/.secret/flag.txt: Permission denied
labex:project/ $ cat /opt/backups/.secret/flag.txt 2>/dev/null
labex:project/ $ sudo cat /opt/backups/.secret/flag.txt            
FLAG{d1r3ctory_tr4v3rs4l_m4st3r}
labex:project/ $ 
```
# Another Mission
## 🏁 Challenge Recap
- **Scenario:** A critical configuration flag (`flag.txt`) was hidden in the filesystem.  
- **Objective:** Locate and display the flag.  
- **Twist:** The file was hidden in a restricted directory with limited permissions.  
- **Flag format:**  
  ```text
  FLAG{...}
  ```

---

## 🔐 Advanced Version
### Approach
- Use `find` to search the entire filesystem.  
- Suppress permission errors with `2>/dev/null`.  
- Escalate privileges with `sudo` to read the file.  

### Commands
```bash
# Search for the flag file
sudo find / -name flag.txt 2>/dev/null

# Output: /opt/backups/.secret/flag.txt

# Check permissions
ls -l /opt/backups/.secret/flag.txt

# Read the file with elevated privileges
sudo cat /opt/backups/.secret/flag.txt
```

### Advanced One‑Liner
```bash
sudo cat $(sudo find / -name flag.txt 2>/dev/null)
```
This combines search + read in a single command.

---

## 🪜 Beginner Version
### Step‑by‑Step Exploration
1. **Explore `/opt` directory**
   ```bash
   ls /opt
   ```
   → Found `backups`.

2. **Enter backups folder**
   ```bash
   cd /opt/backups
   ```

3. **Reveal hidden directories**
   ```bash
   ls -la
   ```
   → Found `.secret`.

4. **Enter hidden directory**
   ```bash
   cd .secret
   ```

5. **Locate flag file**
   ```bash
   ls -la
   ```
   → Found `flag.txt`.

6. **Check permissions**
   ```bash
   ls -l flag.txt
   ```

7. **Read the flag**
   ```bash
   cat flag.txt
   ```
   If restricted:
   ```bash
   sudo cat flag.txt
   ```

---

## 🎯 Key Learnings
- **Directory traversal:** `cd`, `ls`, `ls -la` to explore and reveal hidden files.  
- **File search:** `find / -name flag.txt 2>/dev/null` to locate files system‑wide.  
- **Permissions:** `ls -l` to analyze access restrictions.  
- **Privilege escalation:** `sudo` to bypass permission barriers.  

---

## ✅ Outcome
Both approaches (Advanced + Beginner) lead to the same result:  
```
FLAG{...}
```