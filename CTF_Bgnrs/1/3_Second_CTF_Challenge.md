# 🔐 Weak Password Access Challenge (Advanced) – Q&A Revision

### 1. What is the mission of this challenge?  
**Answer:** To gain access to the **visitor account** using a weak password and then retrieve the hidden **flag file** by displaying its contents in the terminal.

---

### 2. Which Linux command allows you to switch to another user account?  
**Answer:**  
```bash
su visitor
```
This switches to the `visitor` account (you’ll be prompted for its password).

---

### 3. What are weak passwords, and why are they dangerous?  
**Answer:** Weak passwords are simple, guessable strings like `1234`, `password`, or the username itself. They are dangerous because attackers can easily guess them and gain unauthorized access.

---

### 4. What common weak passwords might you try first?  
**Answer:**  
- `visitor`  
- `password`  
- `1234`  
- `admin`  
- `test`  

---

### 5. How can you verify which user account you are currently logged into?  
**Answer:**  
```bash
whoami
```
This prints the username of the current session.

---

### 6. Which command lists all files, including hidden ones, in a directory?  
**Answer:**  
```bash
ls -a
```
The `-a` option shows hidden files (those starting with `.`).

---

### 7. How are hidden files represented in Linux?  
**Answer:** Hidden files begin with a **dot (`.`)**, e.g. `.flag` or `.secret`.

---

### 8. Once you discover the hidden flag file, which command should you use to read its contents?  
**Answer:**  
```bash
cat .flag
```
This displays the flag stored inside the hidden file.

---

### 9. Why is practicing weak password exploitation important in CTF challenges?  
**Answer:** It teaches the risks of poor password practices, highlights the importance of strong authentication, and simulates real‑world attack scenarios.

---

### 10. What Linux skills are tested in this challenge?  
**Answer:**  
- User management (`su`, `whoami`)  
- Password handling (guessing weak credentials)  
- File system navigation (`ls -a`)  
- Content reading (`cat`)  

---

### 11. How does this challenge differ from beginner‑friendly versions?  
**Answer:** No hints are provided, requiring independent problem‑solving and deeper Linux knowledge compared to guided beginner challenges.

---

### 12. What is the final step after gaining access to the visitor account?  
**Answer:** Locate the hidden flag file and use `cat` to display its contents, proving successful completion.

# Code
```bash
labex:project/ $ su visitor
Password: 
visitor@6a4d1c50cd9ff37c016bb526:/home/labex/project$ ls -la
total 4
drwxr-xr-x 1 labex labex    6 Jul 18  2024 .
drwxr-x--- 1 labex labex 4096 Jul  7 23:39 ..
visitor@6a4d1c50cd9ff37c016bb526:/home/labex/project$ cd ../
bash: cd: ../: Permission denied
visitor@6a4d1c50cd9ff37c016bb526:/home/labex/project$ ls ~/ -a
.  ..  .bash_logout  .bashrc  .profile  .secure
visitor@6a4d1c50cd9ff37c016bb526:/home/labex/project$ cat ~/.secure 
cat: /home/visitor/.secure: Is a directory
visitor@6a4d1c50cd9ff37c016bb526:/home/labex/project$ cd ~/.secure
visitor@6a4d1c50cd9ff37c016bb526:~/.secure$ ls -a
.  ..  flag.txt
visitor@6a4d1c50cd9ff37c016bb526:~/.secure$ cat flag.txt
flag{w3ak_p4ssw0rd_d4ng3r}
visitor@6a4d1c50cd9ff37c016bb526:~/.secure$ 
```

# 🔐 Weak Password Summarization

### 1. What did you demonstrate in this challenge?  
**Answer:** How a weak password can lead to a security breach by gaining access to the `visitor` account and reading a sensitive hidden file.

---

### 2. Which command did you practice to switch user contexts?  
**Answer:**  
```bash
su visitor
```
This command switches to the `visitor` account after entering its password.

---

### 3. What basic file system navigation skills were used?  
**Answer:**  
- `ls -a` → to list all files, including hidden ones.  
- `cat .flag` → to read the contents of the hidden flag file.

---

### 4. In the real world, why are weak passwords a major risk?  
**Answer:** Because attackers often exploit weak or default passwords to gain **initial access** to systems, making them one of the most common entry points for breaches.

---

### 5. What security principle does this exercise highlight?  
**Answer:** The **critical importance of enforcing strong password policies** for all user accounts to prevent unauthorized access.

---

### 6. As a security professional, why is this skill valuable?  
**Answer:** Knowing how to test for and identify weak password vulnerabilities is fundamental in **system hardening** and **penetration testing**.

---

### 7. What is the final step in this challenge?  
**Answer:** Successfully displaying the contents of the hidden flag file in the terminal, proving that the weak password was exploited.
