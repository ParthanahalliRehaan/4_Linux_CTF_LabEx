# Code
```bash
labex:project/ $ cd ~/project/secrets
labex:secrets/ $ ls 
labex:secrets/ $ ls -a
.  ..  .secret_flag.txt
labex:secrets/ $ cat .secret_flag.txt
labex-hidden-treasure
```

# 🎉 CTF Challenge Summary
## 🏴 CTF Basics
- **What?** Capture The Flag (CTF) = cybersecurity competitions.  
- **Why?** Learn security concepts through puzzles and hidden flags.  
- **How?** Solve challenges → retrieve secret flags → prove completion.

---

## 🏁 Flag Format
- Flags are secret strings, e.g. `labex{flag_content_here}`.  
- In this challenge: format is `labex-xxxx`.  
- **Why?** Flags confirm you solved the puzzle.  
- **How?** Read files or outputs to find them.

---

## 📂 Hidden Files
- **What?** Files starting with `.` are hidden in Linux.  
- **Why?** Important data (like flags) may be hidden this way.  
- **How?**
  ```bash
  ls -a   # shows all files including hidden ones
  ```

---

## 📄 File Discovery & Content Reading
- **ls -a** → Lists all files (including hidden).  
- **cat filename** → Displays file contents.  
- **Why?** To locate and reveal the flag.  
- **How?**
  ```bash
  ls -a
  cat .hiddenfile
  ```

---

## 🛠️ Skills Learned
- **CTF Concepts** → Understanding competitions & flags.  
- **Flag Recognition** → Identifying correct formats.  
- **Linux Basics** → Hidden files, listing, reading.  
- **Foundation for Cybersecurity** → First step into system administration & security challenges.

---

✅ You’ve now built the **core toolkit** for beginner CTFs:  
- Spot hidden files (`ls -a`)  
- Read contents (`cat`)  
- Recognize flags (`labex-xxxx`) 

