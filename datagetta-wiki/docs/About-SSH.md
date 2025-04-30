# **Understanding SSH on an Ubuntu Server**

## **1️⃣ What is SSH?**
SSH (**Secure Shell**) is a protocol that allows **secure remote access** to a machine over a network. It is **encrypted**, meaning all communication between your computer (client) and the server is **protected from eavesdropping**.

On an **Ubuntu VM/server**, SSH functions as a **client-server system**, where:
- Your **local computer** is the **SSH client**.
- The **Ubuntu VM/server** runs the **SSH server (sshd)**.

---

## **2️⃣ How SSH Works**
### **Step 1: SSH Server (sshd) Runs on the Ubuntu VM**
On the **Ubuntu server**, an SSH daemon (`sshd`) listens for incoming connections **on port 22 (default)**.

To check if SSH is running:
```bash
sudo systemctl status ssh
```
If SSH is not running, start it:
```bash
sudo systemctl start ssh
```
To ensure SSH starts on boot:
```bash
sudo systemctl enable ssh
```

---

### **Step 2: Connecting to the SSH Server from Your Local Machine**
To connect to the Ubuntu server, use the following SSH command from your terminal:
```bash
ssh [your-username]@your-server-ip
```
For example, if connecting to **datagetta_servers**:
```bash
ssh yourusername@datagetta.cse.eng.auburn.edu
```
When this command runs:
1. The SSH client **finds the server's IP address**.
2. It **requests authentication** (password or SSH key).
3. If authentication **succeeds**, an **encrypted session** starts, allowing you to execute commands remotely.

---

## **3️⃣ SSH Authentication Methods**
There are two main ways to authenticate:

### **A) Password Authentication (Less Secure)**
- You enter your **password manually** each time you log in.
- If the server allows password authentication (`PasswordAuthentication yes` in `/etc/ssh/sshd_config`), you will be prompted for a password.

### **B) SSH Key Authentication (More Secure)**
- Instead of passwords, **SSH keys** (public-private key pairs) are used.
- The **private key** stays on your local machine, and the **public key** is added to the server.

---

## **4️⃣ Understanding SSH Keys**
SSH keys provide **passwordless login** and **better security**.

### **Generating SSH Keys**
To generate a new SSH key pair on your **local machine**:
```bash
ssh-keygen -t rsa -b 4096 -C "your-email@example.com"
```
This creates:
- **Private Key (`~/.ssh/id_rsa`)** → **DO NOT share this!**
- **Public Key (`~/.ssh/id_rsa.pub`)** → Can be added to an SSH server for authentication.

---

### **5️⃣ How the Server Uses Your SSH Key**
When you try to log in:
1. The SSH client **sends the public key** to the server.
2. The server **checks if it exists** in `~/.ssh/authorized_keys`.
3. If the key matches, the server **encrypts a challenge message**.
4. Your local machine **decrypts it using your private key** and proves your identity.
5. You are **logged in without needing a password**.

---

## **6️⃣ Setting Up SSH Key Authentication on an Ubuntu Server**
### **Step 1: Copy Your Public Key to the Server**
To allow **passwordless SSH login**, add your key to the server's `authorized_keys` file.

On your **local machine**, run:
```bash
ssh-copy-id yourusername@datagetta.cse.eng.auburn.edu
```
Or manually:
```bash
scp ~/.ssh/id_rsa.pub yourusername@datagetta.cse.eng.auburn.edu:~/
```
Then log into the server:
```bash
ssh yourusername@datagetta.cse.eng.auburn.edu
```
Append the key to `authorized_keys`:
```bash
mkdir -p ~/.ssh
cat ~/id_rsa.pub >> ~/.ssh/authorized_keys
chmod 600 ~/.ssh/authorized_keys
rm ~/id_rsa.pub
```

---

### **Step 2: Disable Password Authentication (For Security)**
Edit the SSH configuration file:
```bash
sudo nano /etc/ssh/sshd_config
```
Find and change:
```
PasswordAuthentication no
PermitRootLogin no
```
Restart SSH for changes to take effect:
```bash
sudo systemctl restart ssh
```

---

## **7️⃣ The `.ssh` Directory on the Server**
After setting up SSH keys, the `~/.ssh/` folder on the server will look like:

```bash
/home/yourusername/.ssh/
├── authorized_keys  # Contains all public keys that are allowed to log in
├── known_hosts      # Keeps a record of previously connected SSH servers
```

To view existing SSH keys:
```bash
ls -la ~/.ssh
```

To check allowed SSH keys:
```bash
cat ~/.ssh/authorized_keys
```

---

## **8️⃣ Secure SSH with a Firewall**
To prevent unauthorized SSH access, configure the firewall:
```bash
sudo ufw allow OpenSSH
sudo ufw enable
sudo ufw status
```
This ensures **only trusted clients** can access your server.

---

## **🛠️ Summary of SSH on Ubuntu**
✅ **SSH Server (`sshd`) runs on port 22**  
✅ **Clients connect via SSH using password or key authentication**  
✅ **SSH Keys provide secure, passwordless login**  
✅ **The `.ssh` folder contains authentication settings**  
✅ **Configuring `sshd_config` improves security**  

---

## **9️⃣ Debugging SSH Issues**
If you are having trouble connecting, check:
```bash
sudo journalctl -u ssh --since "1 hour ago"
```
Or inspect failed login attempts:
```bash
sudo tail -f /var/log/auth.log
```

---

## **🚀 Next Steps**
Would you like to configure **GitHub Actions for secure, passwordless SSH deployments**?  
Let me know if you need **automated SSH key management** for your team!

