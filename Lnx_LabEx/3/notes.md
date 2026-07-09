# 📂 Linux File Viewing & Comparison Commands

## 1. Print Entire File Contents
```bash
cat /tmp/hello
```
- Displays the full contents of the file.  
- Example output:
```
Hi,
I am Labby!
```

---

## 2. Display File Contents with Line Numbers
```bash
cat -n /tmp/hello
```
- `-n` adds line numbers to each line.  
- Useful for referencing specific lines.  
- Example output:
```
     1 Hi,
     2 I am Labby!
```

---

## 3. Print the Top Lines of a File
```bash
head -n1 /tmp/hello
```
- `-n1` shows only the first line.  
- Without `-n`, `head` shows the first 10 lines by default.  
- Example output:
```
Hi,
```

---

## 4. View the First Few Bytes of a File
```bash
head -c1 /tmp/hello
```
- `-c1` shows the first byte (character).  
- Change `1` to any number to view more bytes.  
- Example output:
```
H
```

---

## 5. Print the Last Lines of a File
```bash
tail -n1 /tmp/hello
```
- `-n1` shows only the last line.  
- Without `-n`, `tail` shows the last 10 lines by default.  
- Example output:
```
I am Labby!
```

---

## 6. View the Last Few Bytes of a File
```bash
tail -c1 /tmp/hello
```
- Shows the last byte (often invisible if it’s a newline).  

```bash
tail -c2 /tmp/hello
```
- Shows the last two bytes.  
- Example output:
```
!
```

---

## 7. Comparing Files
```bash
cd ~/project
diff file1 file2
```
- `cd ~/project` → moves into the project directory.  
- `diff file1 file2` → compares two files line by line.  
- Example output:
```
1c1
< this is file1
---
> this is file2
```
- Meaning: Line 1 in file1 must be changed to match line 1 in file2.

---

## 8. Comparing Directories
```bash
diff -r ~/Desktop ~/Code
```
- `-r` → recursively compares subdirectories.  
- Example output:
```
Only in /home/labex/Desktop: code.desktop
Only in /home/labex/Desktop: gedit.desktop
Only in /home/labex/Desktop: gvim.desktop
Only in /home/labex/Desktop: xfce4-terminal.desktop
```
- Shows files present in one directory but not the other.

---

# 📝 Recap
- **`cat`** → View entire file contents (with or without line numbers).  
- **`head`** → View the beginning of a file (by lines or bytes).  
- **`tail`** → View the end of a file (by lines or bytes).  
- **`diff`** → Compare files line by line.  
- **`diff -r`** → Compare directories recursively.  

💡 **Tip:** Use `man <command>` (e.g., `man cat`) to see the manual page for detailed options.  

---

# ⚡ Case-Based Example
```bash
rehaan:~/project$ cat -n file1.txt
```
- Rehaan is inside the `project` directory.  
- This command prints `file1.txt` with line numbers for easy reference.  

---

# 📊 Quick Cheat Sheet

| Command | Purpose | Example Output |
|---------|---------|----------------|
| `cat /tmp/hello` | Show entire file | Hi,<br>I am Labby! |
| `cat -n /tmp/hello` | Show file with line numbers | 1 Hi,<br>2 I am Labby! |
| `head -n1 /tmp/hello` | Show first line | Hi, |
| `head -c1 /tmp/hello` | Show first byte | H |
| `tail -n1 /tmp/hello` | Show last line | I am Labby! |
| `tail -c2 /tmp/hello` | Show last 2 bytes | ! |
| `diff file1 file2` | Compare files | Shows differences line by line |
| `diff -r ~/Desktop ~/Code` | Compare directories | Lists files only in one directory |
