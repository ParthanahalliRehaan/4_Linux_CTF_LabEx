# 🖥️ Basic Commands Cheat Sheet

## 📂 `ls`
- **What?** Lists files and directories in the current folder.  
- **Why?** Helps you see what’s inside a directory (like looking at a folder in File Explorer).  
- **How?**
  ```bash
  ls        # list files
  ls -l     # detailed list with permissions, size, date
  ls -a     # show hidden files (starting with .)
  ```

---

## 📄 `cat`
- **What?** Displays the contents of a file.  
- **Why?** Useful for quickly reading flags or text files without opening an editor.  
- **How?**
  ```bash
  cat file.txt        # show file contents
  cat flag.txt        # often used to reveal the flag
  ```

---

## 🔍 `grep`
- **What?** Searches for text patterns inside files.  
- **Why?** Helps find hidden strings, keywords, or flags in large files.  
- **How?**
  ```bash
  grep "keyword" file.txt       # search for keyword in file
  grep -r "flag" ./             # search recursively in all files in current directory
  ```

---

# 🌐 Network Tools Cheat Sheet

## 🔎 `nmap`
- **What?** Network mapper tool that scans for open ports and services.  
- **Why?** Helps discover what services a target machine is running (web server, SSH, etc.).  
- **How?**
  ```bash
  nmap target.com        # basic scan
  nmap -p 80 target.com  # scan specific port
  nmap -A target.com     # aggressive scan (OS + services)
  ```

---

## 📡 `telnet`
- **What?** Connects to a server on a specific port using plain text.  
- **Why?** Useful for testing connections and interacting with services manually.  
- **How?**
  ```bash
  telnet target.com 80   # connect to web server port
  telnet target.com 23   # connect to telnet service
  ```

---

## 🔑 `ssh`
- **What?** Secure Shell, used to log into remote machines securely.  
- **Why?** Lets you access and control remote systems (often part of challenges).  
- **How?**
  ```bash
  ssh user@target.com        # connect to remote server
  ssh -p 2222 user@target.com # connect on custom port
  ```

---

# ✅ Quick Revision Flow
1. **ls** → See what files exist.  
2. **cat** → Read file contents (flags often hidden here).  
3. **grep** → Search for hidden strings.  
4. **nmap** → Scan target machine for open ports.  
5. **telnet** → Connect to services manually.  
6. **ssh** → Securely log in and explore remote systems.  