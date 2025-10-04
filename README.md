# 🐧 Linux Server Administration Essentials

![Linux](https://img.shields.io/badge/Linux-Ubuntu%20%7C%20CentOS-orange?style=for-the-badge&logo=linux)
![Apache](https://img.shields.io/badge/Web%20Server-Apache%20%7C%20Nginx-red?style=for-the-badge&logo=apache)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

> **Real Linux admin skills, no BS.** Learn how to set up, secure, and manage a Linux web server the way actual sysadmins do it.

## 🎯 What's This About?

If you're serious about IT or cloud computing, you need to know Linux. This lab walks you through setting up a web server from scratch, managing users and permissions, and locking down your server so it doesn't get pwned in 5 minutes.

By the end, you'll have a fully functional, secure Linux web server running in the cloud (or on your local VM).

## 🛠️ Tech Stack

- **Linux** (Ubuntu Server or CentOS—your pick)
- **Apache or Nginx** (web server of choice)
- **SSH** (for remote access)
- **UFW** (Uncomplicated Firewall—because security matters)
- **Git & GitHub** (for version control)

## 🚀 Quick Start

### Step 1: Spin Up a Linux VM
You'll need a Linux virtual machine. Options:
- **Cloud:** AWS EC2, Google Cloud, Azure (free tier works great)
- **Local:** VirtualBox, VMware, or Hyper-V

Make sure SSH is enabled so you can connect remotely.

### Step 2: Clone This Repo

```bash
git clone https://github.com/x0VIER/02-linux-admin.git
cd 02-linux-admin
```

### Step 3: SSH Into Your VM

```bash
ssh -i /path/to/your/key.pem ubuntu@your_vm_ip
```

Replace `your_vm_ip` with your actual VM's IP address.

## 💡 What You'll Learn

- Install and configure a web server (Apache or Nginx)
- Manage users, groups, and sudo privileges
- Set file and directory permissions the right way
- Configure a firewall to block unwanted traffic
- Harden SSH to prevent brute-force attacks
- Deploy a simple static website

## 📂 Project Structure

```
02-linux-admin/
├── web_content/
│   └── index.html          # Your static website
├── setup_script.sh          # Optional automation script
└── README.md
```

## 🎮 Lab Tasks

### Task 1: Install and Configure a Web Server

Pick your weapon—Apache or Nginx—and get it running.

**For Apache:**
```bash
sudo apt update
sudo apt install apache2 -y
sudo systemctl start apache2
sudo systemctl enable apache2
```

**For Nginx:**
```bash
sudo apt update
sudo apt install nginx -y
sudo systemctl start nginx
sudo systemctl enable nginx
```

Copy the `index.html` file from `web_content/` to your web server's root directory (usually `/var/www/html/`).

### Task 2: User and Permission Management

Create a non-root user and give them the right permissions.

```bash
# Create a new user
sudo adduser webadmin

# Grant sudo privileges
sudo usermod -aG sudo webadmin

# Change ownership of web content
sudo chown -R webadmin:webadmin /var/www/html
sudo chmod -R 755 /var/www/html
```

**Pro tip:** Configure sudoers to allow `webadmin` to restart the web server without a password.

### Task 3: Lock Down Your Server

Security isn't optional. Here's how to harden your setup:

**Enable UFW and allow only necessary ports:**
```bash
sudo ufw allow 22/tcp    # SSH
sudo ufw allow 80/tcp    # HTTP
sudo ufw allow 443/tcp   # HTTPS
sudo ufw enable
```

**Disable password authentication for SSH:**
Edit `/etc/ssh/sshd_config`:
```
PasswordAuthentication no
PubkeyAuthentication yes
```

Restart SSH:
```bash
sudo systemctl restart sshd
```

**(Optional) Change the default SSH port:**
Edit `/etc/ssh/sshd_config` and change `Port 22` to `Port 2222`, then restart SSH.

## 🏆 Success Criteria

You'll know you crushed it when:
- Your web server is up and serving the `index.html` page
- You can access the site via your VM's public IP
- SSH is hardened (key-based auth only, custom port)
- UFW is active and blocking everything except SSH, HTTP, and HTTPS
- You've documented every step with screenshots or command output

## 🤝 Contributing

Got improvements? Found a bug? PRs are welcome! Fork this repo, make your changes, and submit a pull request.

## 📄 License

MIT License - use this however you want. Just don't blame me if you lock yourself out of your server 😅

## 🔗 Connect

Built by someone who's locked themselves out of too many servers. Learn from my mistakes!

---

**Keywords:** Linux administration, web server setup, Apache, Nginx, SSH hardening, UFW firewall, Linux security, server management, Ubuntu, CentOS, DevOps, sysadmin
