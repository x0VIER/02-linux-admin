# Lab 02: Linux Server Administration Essentials

## Overview

This lab focuses on fundamental Linux server administration skills crucial for IT professionals. Participants will set up and configure a basic web server, manage users and permissions, and implement essential security measures, demonstrating their ability to maintain a secure and functional Linux environment.

## Technologies Used

*   Linux (e.g., Ubuntu, CentOS)
*   Apache HTTP Server or Nginx
*   SSH
*   UFW (Uncomplicated Firewall)
*   Git & GitHub

## Learning Objectives

Upon completion of this lab, you will be able to:

*   Install and configure a web server (Apache or Nginx) on a Linux instance.
*   Manage user accounts and groups, including sudo privileges.
*   Set and understand file and directory permissions.
*   Implement basic firewall rules using UFW.
*   Harden SSH access for improved security.
*   Deploy a simple static website.

## Lab Structure

```
.gitignore
README.md
setup_script.sh  # Optional: for automating initial setup
web_content/     # Directory for static website files
└── index.html
```

## Setup Instructions

1.  **Provision a Linux Virtual Machine:**
    *   Use a cloud provider (AWS EC2, Google Cloud, Azure) or a local virtualization software (VirtualBox, VMware) to create a new Linux VM (e.g., Ubuntu Server).
    *   Ensure SSH access is configured.

2.  **Clone the Repository (on your local machine, then transfer content to VM or clone directly on VM):**
    ```bash
    git clone https://github.com/your-username/02-linux-admin.git
    cd 02-linux-admin
    ```

3.  **Connect to your Linux VM via SSH:**
    ```bash
    ssh -i /path/to/your/key.pem ubuntu@your_vm_ip
    ```

## Lab Tasks

### Task 1: Web Server Installation and Configuration

*   Install either Apache or Nginx web server.
*   Configure the web server to serve a simple `index.html` file from the `web_content/` directory.
*   Ensure the web server starts automatically on boot.

### Task 2: User and Permission Management

*   Create a new non-root user account (e.g., `webadmin`).
*   Grant `webadmin` sudo privileges without requiring a password for specific commands (e.g., restarting the web server).
*   Change ownership and permissions of the `web_content/` directory so that the web server can read files, but only `webadmin` can modify them.

### Task 3: Basic Security Measures

*   Configure UFW to allow only SSH (port 22), HTTP (port 80), and HTTPS (port 443) traffic.
*   Disable password authentication for SSH and enforce key-based authentication.
*   Change the default SSH port from 22 to a non-standard port (e.g., 2222).

## Expected Outcome

By the end of this lab, you will have a functional and basic secure Linux web server. Your `README.md` should include detailed steps taken, commands used, and screenshots/output demonstrating successful configuration. The simple website should be accessible via the VM's public IP address.

## Contribution

Feel free to fork this repository, implement your solutions, and submit pull requests. Constructive feedback and improvements are always welcome.

## License

This project is licensed under the MIT License - see the `LICENSE` file for details.

