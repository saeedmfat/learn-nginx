### Here’s how to **start, stop, and restart** Nginx on Ubuntu, along with additional useful commands:

---

### **1. Start Nginx**
```bash
sudo systemctl start nginx
```
- **Use case**: When Nginx is stopped and you want to start it.

---

### **2. Stop Nginx**
```bash
sudo systemctl stop nginx
```
- **Use case**: When you need to temporarily shut down the web server.

---

### **3. Restart Nginx**
```bash
sudo systemctl restart nginx
```
- **Use case**: After making configuration changes (e.g., editing `/etc/nginx/sites-available/default`).

---

### **4. Reload Nginx (Without Dropping Connections)**
```bash
sudo systemctl reload nginx
```
- **Use case**: For applying config changes gracefully (no downtime).

---

### **5. Check Nginx Status**
```bash
sudo systemctl status nginx
```
- **Output**:
  - ✅ `active (running)` = Working correctly.
  - ❌ `inactive (dead)` = Not running.
  - 🔄 `failed` = Check logs with `sudo journalctl -xe`.

---

### **6. Enable Nginx (Start at Boot)**
```bash
sudo systemctl enable nginx
```
- Ensures Nginx starts automatically when the system reboots.

---

### **7. Disable Nginx (Prevent Auto-Start)**
```bash
sudo systemctl disable nginx
```
- Stops Nginx from launching on boot (but doesn’t stop it now).

---

### **8. Test Nginx Configuration (Before Restarting)**
```bash
sudo nginx -t
```
- Checks for syntax errors in config files.  
- **Success output**:  
  ```
  nginx: configuration file /etc/nginx/nginx.conf test is successful
  ```

---

### **9. Force Stop Nginx (If Frozen)**
```bash
sudo systemctl kill -s SIGKILL nginx
```
- **Use case**: Only if `stop` or `restart` fail.

---

### **Summary Table**
| Command                     | Action                                      |
|-----------------------------|--------------------------------------------|
| `sudo systemctl start nginx`   | Starts Nginx                               |
| `sudo systemctl stop nginx`    | Stops Nginx                                |
| `sudo systemctl restart nginx` | Restarts Nginx (hard)                      |
| `sudo systemctl reload nginx`  | Reloads configs gracefully (no downtime)   |
| `sudo systemctl status nginx`  | Shows if Nginx is running                  |
| `sudo nginx -t`               | Tests config files for errors              |

---

### **Troubleshooting Tips**
- If Nginx fails to start:  
  ```bash
  sudo tail -n 20 /var/log/nginx/error.log
  ```
- If port 80 is blocked:  
  ```bash
  sudo ss -tulnp | grep ':80'
  ```

### **Task 3 : Enable Nginx to Start on Boot**  
To ensure Nginx starts automatically when your system boots up, run:  

```bash
sudo systemctl enable nginx
```

**Verify it’s enabled:**  
```bash
sudo systemctl is-enabled nginx
```
- ✅ Expected output: `enabled`  

---