### Here's a step-by-step guide to install the latest version of **Nginx** on the latest **Ubuntu** (assuming Ubuntu 22.04 LTS or later):

---

### **Step 1: Update System Packages**
Before installing Nginx, update your Ubuntu package index:
```bash
sudo apt update
sudo apt upgrade -y
```

---

### **Step 2: Install Nginx**
Install Nginx using `apt`:
```bash
sudo apt install nginx -y
```

---

### **Step 3: Verify Installation**
Check if Nginx is installed and running:
```bash
sudo systemctl status nginx
```
(You should see `active (running)` in the output.)

---

### **Step 4: Allow Nginx in Firewall**
If you have `ufw` (firewall) enabled, allow HTTP (80) and HTTPS (443):
```bash
sudo ufw allow 'Nginx Full'
sudo ufw enable  # (if not already enabled)
sudo ufw status  # Verify rules
```

---

### **Step 5: Test Nginx**
Open a web browser and visit:
```
http://your-server-ip
```
(Replace `your-server-ip` with your server's actual IP or `localhost` if testing locally.)

You should see the **Nginx welcome page** (confirms successful installation).

---

### **Step 6: Manage Nginx Service**
- **Start Nginx**:  
  ```bash
  sudo systemctl start nginx
  ```
- **Stop Nginx**:  
  ```bash
  sudo systemctl stop nginx
  ```
- **Restart Nginx** (after config changes):  
  ```bash
  sudo systemctl restart nginx
  ```
- **Enable Nginx to start on boot**:  
  ```bash
  sudo systemctl enable nginx
  ```

---

### **Optional: Install Latest Nginx from Official Repository**
If you want the **very latest stable/mainline version** (instead of Ubuntu’s default repo), follow these steps:

1. Add the official Nginx repository:
   ```bash
   sudo apt install curl gnupg2 ca-certificates lsb-release ubuntu-keyring
   curl https://nginx.org/keys/nginx_signing.key | gpg --dearmor | sudo tee /usr/share/keyrings/nginx-archive-keyring.gpg >/dev/null
   echo "deb [signed-by=/usr/share/keyrings/nginx-archive-keyring.gpg] http://nginx.org/packages/ubuntu $(lsb_release -cs) nginx" | sudo tee /etc/apt/sources.list.d/nginx.list
   ```

2. Install Nginx:
   ```bash
   sudo apt update
   sudo apt install nginx -y
   ```

### **Done!**

