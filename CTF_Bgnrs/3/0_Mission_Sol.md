# Code
```bash
2024-07-18 11:41:37 startup packages configure
labex:log/ $ cd /var/log
labex:log/ $ ls -la
total 1948
drwxr-xr-x 1 root    root                 70 Jul  9 10:51 .
drwxr-xr-x 1 root    root                 28 Jul 18  2024 ..
-rw-r--r-- 1 root    root             130630 Jul 18  2024 alternatives.log
drwxr-x--- 2 root    adm                  72 Jul 18  2024 apache2
drwxr-xr-x 3 root    root                 20 Jul  9 10:51 application
drwxr-xr-x 1 root    root                 60 Jul 18  2024 apt
-rw-r--r-- 1 root    root              64549 Jun 27  2024 bootstrap.log
-rw-rw---- 1 root    utmp                  0 Jun 27  2024 btmp
-rw-r--r-- 1 root    root            1378821 Jul 18  2024 dpkg.log
-rw-r--r-- 1 root    root              32000 Jul 18  2024 faillog
-rw-r--r-- 1 root    root               3501 Jul 18  2024 fontconfig.log
drwxr-sr-x 2 root    systemd-journal       6 Jul 18  2024 journal
-rw-rw-r-- 1 root    utmp            1460292 Jul  9 10:53 lastlog
drwxr-xr-x 2 mongodb mongodb               6 Jul 18  2024 mongodb
drwxr-s--- 2 mysql   mysql                 6 Jul 18  2024 mysql
drwxr-xr-x 2 root    adm                  41 Jul 18  2024 nginx
drwx------ 2 root    root                  6 Jul 18  2024 private
drwxr-s--- 2 redis   adm                   6 Jul 18  2024 redis
drwxr-xr-x 1 root    root               4096 Jul  9 10:51 supervisor
drwxr-x--- 2 root    adm                   6 Jan 15  2022 unattended-upgrades
-rw-rw-r-- 1 root    utmp               1536 Jul  9 10:53 wtmp
labex:log/ $ grep -R "FLAG" /var/log
grep: /var/log/apt/term.log: Permission denied
grep: /var/log/btmp: Permission denied
grep: /var/log/supervisor/ssh-stdout---supervisor-ykqurptz.log: Permission denied
grep: /var/log/supervisor/ssh-stderr---supervisor-dbv0adls.log: Permission denied
grep: /var/log/supervisor/ttyd-stdout---supervisor-kl5sc_vo.log: Permission denied
grep: /var/log/supervisor/ttyd-stderr---supervisor-6t94c6vq.log: Permission denied
grep: /var/log/supervisor/vnc-stdout---supervisor-s1lx75gj.log: Permission denied
grep: /var/log/supervisor/vnc-stderr---supervisor-rc7sul88.log: Permission denied
grep: /var/log/supervisor/webide-stdout---supervisor-fxjzy8cw.log: Permission denied
grep: /var/log/supervisor/webide-stderr---supervisor-1q1ilm9e.log: Permission denied
grep: /var/log/application/backup/system_audit_2023-10-27.log: Permission denied
grep: /var/log/apache2: Permission denied
grep: /var/log/mysql: Permission denied
grep: /var/log/nginx/access.log: Permission denied
grep: /var/log/nginx/error.log: Permission denied
grep: /var/log/redis: Permission denied
grep: /var/log/private: Permission denied
grep: /var/log/unattended-upgrades: Permission denied
grep: labex:log/ $ sudo grep -R "FLAG" /var/log
/var/log/application/backup/system_audit_2023-10-27.log:[2023-10-27 10:00:04] INFO: Secret key for deployment: FLAG{LogDive005}
labex:log/ $ 
```
# Explanation of Mission
## 🏁 Introduction
- You’re acting as a **Junior System Administrator** in a simulated fast‑paced tech company.  
- Your onboarding challenge: **find a secret flag hidden in `/var/log`**.  
- Purpose: practice real‑world log file analysis skills using Linux command‑line tools.

---

## 🔐 Advanced Challenge
- Task: Locate the flag in `/var/log` without hints.  
- Tools needed:  
  - `ls`, `cd` → navigation  
  - `grep -R` → recursive search  
  - `cat`, `less`, `tail` → view contents  
  - `zgrep` → search compressed logs  
- Flag format:  
  ```text
  FLAG{...}
  ```

---

## 📂 Directory Listing You Shared
You showed the contents of `/var/log`, including:
- Large files: `dpkg.log`, `alternatives.log`, `bootstrap.log`, `faillog`, `lastlog`
- Service directories: `apache2`, `nginx`, `supervisor`, `application`, `mysql`, `redis`
- Special/binary files: `wtmp`, `btmp`, `lastlog`

---

## 🚧 Permission Denied Issue
When running `grep -R "FLAG" /var/log`, you hit multiple **Permission denied** errors.  
Solution: use `sudo` to elevate privileges.

```bash
sudo grep -R "FLAG" /var/log
```

Optional: exclude binary files to reduce noise:
```bash
sudo grep -R "FLAG" /var/log --exclude=wtmp --exclude=btmp --exclude=lastlog
```

---

## 🎯 Likely Flag Locations
- **Supervisor logs** (`/var/log/supervisor/...`) → stdout/stderr of services.  
- **Application logs** (`/var/log/application/...`) → e.g., `system_audit_2023-10-27.log`.  
- **Web server logs** (`apache2`, `nginx`) → access/error logs.  
- **dpkg.log** → package installation logs.

---

## 🪜 Beginner Version Walkthrough
Tasks:
1. Navigate:
   ```bash
   cd /var/log
   ```
2. Search recursively:
   ```bash
   grep -r "FLAG" .
   ```
3. Use `sudo` if needed:
   ```bash
   sudo grep -r "FLAG" .
   ```
4. Identify the flag line:
   ```
   ./application/somefile.log: FLAG{secret_value_here}
   ```
5. Display the flag cleanly:
   ```bash
   sudo grep "FLAG" /var/log/application/somefile.log
   ```

---

## 📌 Where We Stand
- You’ve explored both **advanced** and **beginner** approaches.  
- You know how to handle **permissions** and **binary files**.  
- You’re ready to run the final command to reveal the flag.  
