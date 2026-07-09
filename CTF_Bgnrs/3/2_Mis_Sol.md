```bash
labex:~/ $ cd project
labex:project/ $ cd ..
labex:~/ $ ls -la
drwxrwxr-x 1 labex labex   123 Jul  9 11:07 .cache
OLDPWD=/home/labex/.config
PATH=/usr/lib/jvm/java-11-openjdk-amd64/bin:/usr/lib/jvm/java-11-openjdk-amd64/bin:/usr/lib/jvm/java-11-openjdk-amd64/bin:/usr/lib/jvm/java-11-openjdk-amd64/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/home/labex/.local/bin:/usr/local/go/bin:/home/labex/golang/bin:/usr/share/maven/bin:/usr/local/bin:/usr/sbin/nodejs/bin:/usr/sbin/yarn/bin:/home/labex/.local/bin:/usr/local/go/bin:/home/labex/golang/bin:/usr/share/maven/bin:/usr/local/bin:/usr/sbin/nodejs/bin:/usr/sbin/yarn/bin
PWD=/home/labex/project
SHELL=/usr/bin/zsh
SHLVL=2
TERM=screen
TERM_PROGRAM=tmux
TERM_PROGRAM_VERSION=3.2a
TMUX=/tmp/tmux-5000/default,276,1
TMUX_PANE=%1
USER=labex
_=/usr/bin/env
ZSH=/home/labex/.oh-my-zsh
PAGER=less
LESS=-R
LSCOLORS=Gxfxcxdxbxegedabagacad
LS_COLORS=no=00:fi=00:di=01;34:ln=00;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=41;33;01:ex=00;32:*.cmd=00;32:*.exe=01;32:*.com=01;32:*.bat=01;32:*.btm=01;32:*.dll=01;32:*.tar=00;31:*.tbz=00;31:*.tgz=00;31:*.rpm=00;31:*.deb=00;31:*.arj=00;31:*.taz=00;31:*.lzh=00;31:*.lzma=00;31:*.zip=00;31:*.zoo=00;31:*.z=00;31:*.Z=00;31:*.gz=00;31:*.bz2=00;31:*.tb2=00;31:*.tz2=00;31:*.tbz2=00;31:*.avi=01;35:*.bmp=01;35:*.fli=01;35:*.gif=01;35:*.jpg=01;35:*.jpeg=01;35:*.mng=01;35:*.mov=01;35:*.mpg=01;35:*.pcx=01;35:*.pbm=01;35:*.pgm=01;35:*.png=01;35:*.ppm=01;35:*.tga=01;35:*.tif=01;35:*.xbm=01;35:*.xpm=01;35:*.dl=01;35:*.gl=01;35:*.wmv=01;35:*.aiff=00;32:*.au=00;32:*.mid=00;32:*.mp3=00;32:*.ogg=00;32:*.voc=00;32:*.wav=00;32:*.patch=00;34:*.o=00;32:*.so=01;35:*.ko=01;31:*.la=00;33
PROMPT_EOL_MARK=
XDG_SESSION_TYPE=X11
JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64
JRE_HOME=/usr/lib/jvm/java-11-openjdk-amd64
CLASSPATH=.:/usr/lib/jvm/java-11-openjdk-amd64/lib:/usr/lib/jvm/java-11-openjdk-amd64/lib
GOPATH=/home/labex/golang
GOROOT=/usr/local/go
GOBIN=/home/labex/golang/bin
MAVEN_HOME=/usr/share/maven
MAVEN_CONFIG=/home/labex/.m2
CATALINA_HOME=/opt/apache-tomcat-8.5.54
NODE_HOME=/usr/sbin/nodejs
NODE_PATH=/usr/sbin/nodejs/lib/node_modules
YARN_HOME=/usr/sbin/yarn
SCRIPT_RUNNING=1
FAKE_FLAG=not_the_real_flag
SECRETFLAG=another_fake_flag
MY_SECRET=try_again_later
labex:project/ $ printenv | grep labex
HOME=/home/labex
LOGNAME=labex
MAIL=/var/mail/labex
OLDPWD=/home/labex
PATH=/usr/lib/jvm/java-11-openjdk-amd64/bin:/usr/lib/jvm/java-11-openjdk-amd64/bin:/usr/lib/jvm/java-11-openjdk-amd64/bin:/usr/lib/jvm/java-11-openjdk-amd64/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/home/labex/.local/bin:/usr/local/go/bin:/home/labex/golang/bin:/usr/share/maven/bin:/usr/local/bin:/usr/sbin/nodejs/bin:/usr/sbin/yarn/bin:/home/labex/.local/bin:/usr/local/go/bin:/home/labex/golang/bin:/usr/share/maven/bin:/usr/local/bin:/usr/sbin/nodejs/bin:/usr/sbin/yarn/bin
PWD=/home/labex/project
USER=labex
ZSH=/home/labex/.oh-my-zsh
GOPATH=/home/labex/golang
GOBIN=/home/labex/golang/bin
MAVEN_CONFIG=/home/labex/.m2
labex:project/ $ printenv | grep "labex{"
labex:project/ $ cd ~
labex:~/ $ printenv | grep "labex{"
labex:~/ $ bash
labex@6a4f1063cd9ff37c016f4301:~$ printenv | grep "labex{"
HIDDEN_FLAG=labex{b4sh_0nly_fl4g}
SECRET_FLAG=labex{3nv_v4r_l34k_d3t3ct3d}
labex@6a4f1063cd9ff37c016f4301:~$ echo $SECRET_FLAG
labex{3nv_v4r_l34k_d3t3ct3d}
```
# Another Mission
## 🏁 Mission Recap
- **Objective:** Locate and display secret flags hidden in environment variables.  
- **Flag format:**  
  ```text
  labex{...}
  ```  
- **Twist:** No hints, decoys present, and some flags only visible in specific shells.

---

## 🔧 Techniques You Practiced
### 1. Inspecting Environment Variables
- Commands used:
  ```bash
  printenv
  env
  ```
- These dump all variables currently set in your shell session.

### 2. Filtering for Flags
- Initial search:
  ```bash
  printenv | grep labex
  ```
  → Showed variables like `HOME=/home/labex`, `LOGNAME=labex`, `USER=labex`.  
Here’s a **comprehensive summary** of everything you learned and practiced in the **Environment Variable Leak Challenge (Advanced Version)** — including the switching between shells insight:

---

## 🏁 Challenge Recap
- **Mission:** Find hidden flags in environment variables.  
- **Expected format:**  
  ```text
  labex{...}
  ```  
- **Twist:** Decoys and misleading variables are present, requiring careful filtering.

---

## 🔧 Techniques You Practiced
1. **Listing environment variables**  
   - Commands used:
     ```bash
     printenv
     ```
     or
     ```bash
     env
     ```
   - These dump all environment variables currently set in the shell.

2. **Filtering with grep**  
   - First attempt:
     ```bash
     printenv | grep labex
     ```
     → Showed variables like `HOME=/home/labex`, `LOGNAME=labex`, `USER=labex`.  
     These contained “labex” but not in the correct flag format.

   - Refined search:
     ```bash
     printenv | grep "labex{"
     ```
     → Ensures only variables containing the actual flag format `labex{...}` are displayed.

3. **Handling Decoys**  
   - You encountered misleading variables:
     - `FAKE_FLAG=not_the_real_flag`  
     - `SECRETFLAG=another_fake_flag`  
     - `MY_SECRET=try_again_later`  
   - These were designed to test your filtering skills.

4. **Variable Expansion**  
   - Once a flag variable is found, you can display it with:
     ```bash
     echo $VARIABLE_NAME
     ```

---

## 🪜 New Skill Learned: Switching Shells
- Environment variables can differ between shells (`bash`, `zsh`, etc.).  
- Some flags may only be visible in one shell session.  
- You learned to **switch shells** to uncover hidden flags:
  ```bash
  bash
  printenv | grep "labex{"
  ```
- If needed, return to your original shell:
  ```bash
  exit
  ```

---

## ⚡ Advanced Shortcut
One‑liner to directly find and display all flags:
```bash
printenv | grep "labex{"
```

---

## 🎯 Key Learnings
- **Environment inspection:** `printenv`, `env`, `export -p`.  
- **Filtering:** Use `grep "labex{"` to avoid false positives.  
- **Decoys:** Recognize misleading variables that look like flags but aren’t.  
- **Shell differences:** Flags may only appear in certain shells, so switching (`bash`, `zsh`) is essential.  
- **Privilege of exploration:** Sometimes the challenge is about knowing *where* to look, not just *how*.

---

## ✅ Outcome
- You confirmed that **no valid flags were visible in zsh**.  
- You learned that **switching to bash** (or another shell) is the next step to uncover hidden flags.  
- Once found, the flag will appear in the correct format:
  ```
  labex{secret_value_here}
  ```
