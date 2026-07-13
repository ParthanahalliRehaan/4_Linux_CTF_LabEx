# Code!
```bash
labex:project/ $ nmap localhost
--
labex:project/ $ curl http://localhost:9000/
<head>
<li><a href="session/">session/</a></li>
<li><a href="ssh-XXXXXXRwsNqo/">ssh-XXXXXXRwsNqo/</a></li>
<li><a href="tmux-5000/">tmux-5000/</a></li>
<li><a href="wzpVHVbl/">wzpVHVbl/</a></li>
<li><a href="XJYUTPUI/">XJYUTPUI/</a></li>
</ul>
<hr>
</body>
</html>            
labex:project/ $ curl "http://127.0.0.1:9000/form.html" 
<!DOCTYPE html>
<html>
<head>
    <title>Secret Form</title>
</head>
<body>
    <h1>Enter the Secret Code</h1>
    <form action="/form.html" method="post">
        <label for="secret">Secret:</label>
        <input type="text" id="secret" name="secret"><br><br>
        <input type="submit" value="Submit">
    </form>
</body>
</html>
labex:project/ $ curl http://127.0.0.1:9000/form.html  
<!DOCTYPE html>
<html>
<head>
    <title>Secret Form</title>
</head>
<body>
    <h1>Enter the Secret Code</h1>
    <form action="/form.html" method="post">
        <label for="secret">Secret:</label>
        <input type="text" id="secret" name="secret"><br><br>
        <input type="submit" value="Submit">
    </form>
</body>
</html>
labex:project/ $ curl -X POST "http://127.0.0.1:9000/form.html" -d "secret=' OR '1='1"
Incorrect secret. Try again.                                                                                                             
labex:project/ $ curl -X POST "http://127.0.0.1:9000/form.html" -d "secret=unlock"    
Success! Here is your flag: FLAG{WebInput010}     
```                                                                                                                 
# Mission
## 🗂 Mission Instructions
1. **Identify the running service**  
   - Use `netstat` or `nmap` to discover open ports.  
   - Confirmed that `server.py` was listening on **port 9000**.

2. **Locate the vulnerable form**  
   - Navigated to `http://127.0.0.1:9000/`.  
   - Found `form.html` containing the input field named **`secret`**.

3. **Interact with the form**  
   - Tested normal and injection payloads.  
   - Learned the backend was expecting a specific keyword rather than arbitrary SQL injection.

4. **Submit the unlocking value**  
   - Entered `unlock` into the `secret` field.  
   - This triggered the backend to reveal the hidden flag.

---

## 🏁 Mission Output
The application returned the flag in the required format:

```
FLAG{WebInputXXX}
```

---

### 🎯 Key Takeaway
- The challenge combined **service discovery** (finding the correct port) with **input exploitation** (discovering the right keyword).  
- Instead of complex injection, the solution was a **logic bypass** using the keyword `unlock`.  
- Final success was achieved by submitting `secret=unlock` via the UI (or with curl using `-d "secret=unlock"`).
