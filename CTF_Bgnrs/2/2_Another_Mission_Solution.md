# 🔐 Misconfigured File Permissions Challenge (Advanced Version)

## 🎯 Mission
- You have shell access as a **regular user** (no sudo).
- A sensitive flag is hidden in `/etc/secret`.
- The flag file is protected by strict permissions.
- Your goal: exploit **misconfigured file permissions** to read the flag.

---

## 🛠️ Key Concepts
- **Linux file permissions**: `r` (read), `w` (write), `x` (execute).
- **Owner / Group / Others**: Permissions are divided into these three categories.
- **Misconfiguration**: If the file or directory is world-readable (`r--` for others) or group-readable, you may be able to access it without root.

---

## 📝 Step-by-Step Workflow

### Step 1: Inspect the Directory
```bash
ls -l /etc/secret
```
- Look at the permissions of files inside.
- Example output:
  ```
  -rw-r--r--  1 root root  42 Jul  8  flag.txt
  ```
- If you see `r--` for *others* or your *group*, you can read it.

---

### Step 2: Check Group Membership
```bash
groups
```
- See which groups your user belongs to.
- If the file is readable by one of your groups, you can access it.

---

### Step 3: Attempt to Read the Flag
```bash
cat /etc/secret/flag.txt
```
- If permissions allow, the flag will be revealed:
  ```
  labex{misconfigured_permissions_flag}
  ```

---

### Step 4: Exploit Misconfiguration
- If the file isn’t directly readable:
  - Check if the **directory** has world-readable/executable permissions (`drwxr-xr-x`).
  - Sometimes you can copy or move the file if write permissions are misconfigured.
  - Example:
    ```bash
    cp /etc/secret/flag.txt /tmp/
    cat /tmp/flag.txt
    ```

---

## ⚠️ Important Notes
- You **cannot use sudo** here — the challenge is about exploiting weak permissions.
- Always check both the **file** and **directory** permissions.
- The flag format is:
  ```
  labex{...}
  ```

---

## ✅ Expected Outcome
By finding a misconfigured file (world-readable or group-readable), you’ll be able to read its contents and capture the flag:
```
labex{critical_permission_vulnerability}
```
# Explanation of new things learnt
## 🎯 Mission Recap
- You’re a **regular user** (`labex`) with **no sudo privileges**.  
- A sensitive flag is hidden in `/etc/secret/flag.txt`.  
- The file is deliberately misconfigured with restrictive permissions.  
- Your job: inspect, understand, and manipulate permissions to read the flag.

---

## 🛠️ New Things You Learned

### 1. Permission Strings (`ls -l`)
When you run `ls -l`, you see something like:
```
-rw-r--r--
```

This breaks down as:
- **First character**: file type (`-` = file, `d` = directory).  
- **Next 3 (owner)**: permissions for the file’s owner.  
- **Next 3 (group)**: permissions for the group.  
- **Last 3 (others)**: permissions for everyone else.  

Each position can be:
- `r` = read  
- `w` = write  
- `x` = execute  
- `-` = no permission  

---

### 2. Example: `-r-----r-`
- `-` → regular file  
- `r--` (owner) → owner can read  
- `---` (group) → group has no permissions  
- `r-` (others) → others can read  

So: both the **owner** and **others** can read the file, but nobody can write or execute it.

---

### 3. Why `chmod o+r` Didn’t Work
- `chmod o+r` adds read permission for **others**.  
- But in your screenshot, `flag.txt` was owned by `labex` with **no permissions at all** (`----------`).  
- Since you’re the **owner**, you needed to give **yourself** permission, not “others.”  
- Correct command:  
  ```bash
  chmod u+r flag.txt
  ```

---

## ✅ Solution Workflow

```bash
# Step 1: Navigate to the directory
cd /etc/secret

# Step 2: Inspect permissions
ls -l
# You saw: ---------- 1 labex labex 31 Jul 8 flag.txt

# Step 3: Add read permission for the owner (you)
chmod u+r flag.txt

# Step 4: Verify permissions
ls -l
# Now should show: -r-------- 1 labex labex 31 Jul 8 flag.txt

# Step 5: Read the flag
cat flag.txt
```

Expected output:
```
labex{...}
```

---

## ⚠️ Key Takeaways
- **Owner (u)**, **Group (g)**, **Others (o)** are the three categories in Linux permissions.  
- `chmod u+r` → give owner read access.  
- `chmod g+r` → give group read access.  
- `chmod o+r` → give others read access.  
- Octal notation (like `chmod 644`) is another way to set permissions, mapping numbers to `rwx`.  
# Code
```bash
labex:project/ $ cd /etc/secret
labex:project/etc/secret $ ls -l
total 8
-rw-r----- 1 root  root   42 Jul  8  decoy.conf
---------- 1 labex labex 31 Jul  8  flag.txt

# At first, flag.txt has no permissions at all (----------)

labex:project/etc/secret $ chmod u+r flag.txt
labex:project/etc/secret $ ls -l
total 8
-rw-r----- 1 root  root   42 Jul  8  decoy.conf
-r-------- 1 labex labex 31 Jul  8  flag.txt

# Now the owner (labex) has read permission

labex:project/etc/secret $ cat flag.txt
labex{misconfigured_permissions_flag}
labex:project/etc/secret $
```
