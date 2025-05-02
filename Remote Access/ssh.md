# SSH Setup: Windows 11 (Client) to Ubuntu (Server)

## Introduction

This section demonstrates how to set up a basic SSH connection between a **Windows 11** administrator machine and an **Ubuntu VM** acting as the SSH server.  
SSH (Secure Shell) is a **client-server protocol** commonly used for secure remote administration of Linux systems.
> ⚠️ Important: This type of SSH connection should not be exposed to the Internet without proper security hardening. It is intended for use within a local or virtual lab network only.

- **Client**: Windows 11 (built-in OpenSSH client)
- **Server**: Ubuntu VM with `openssh-server` installed and configured

---

## Setting Up the SSH Server on Ubuntu (Server)

### Step 1: Install and Enable SSH

Open the Ubuntu terminal and run:

```bash
# Install OpenSSH server
sudo apt update
sudo apt install openssh-server

# Enable and start the SSH service
sudo systemctl enable ssh
sudo systemctl start ssh

# Check SSH service status
sudo systemctl status ssh


```bash
# install openssh-server software
$ sudo apt install openssh-server    
$ ssh status
# Enabling and start ssh server
$ sudo systemctl enable ssh
$ sudo systemctl start ssh
$ sudo systemctl status ssh
```
![SSH_status](https://github.com/vitaliizghonnik/it-support-ticketing-lab/blob/main/Remote%20Access/screenshoots/ssh_screenshoots/ssh%20status%20on%20Ubuntu%20VM-1.png)

### Step 2: Allow SSH through the UFW
Enable new firewall rule for the SSH traffic via adding that rule to universal default firewall UFW in Ubuntu

```bash
# Allow SSH though firewall
$ sudo ufw allow ssh
$ sudo ufw status
# Enable the firewall
$ sudo ufw enable
# Check status
$ sudo ufw status
```
![Firewall_status_UFW](https://github.com/vitaliizghonnik/it-support-ticketing-lab/blob/main/Remote%20Access/screenshoots/adding%20rule%20and%20anable%20ufw.png)

### Step 3: Identify the IP Address of the Server (Ubuntu VM)
Open CLI and enter the following command:
`ip a` and look for address initiated by `inet` for instance: 192.168.55.10/24

## Setting up SSH Client on Windows 11

1. Open Command Prompt.
2. Connect to the Ubuntu server using its IP address: 
```bash
ssh username@192.168.55.10
```
3. However instead of using a password for establishing ssh connection, it's better to use a key pair approach, that is more secure authentication approach and commonly used in production environment. 

    - Open `CMD` on a client machine, in this case **Windows 11 Enterprise** and copy the consistence of id_pad by typing the following command:
    ```bash
    # Generate a key pair by typing the following command:
    ssh-keygen
    # Find the location of the generated key pair:
    cd .ssh
    # Copy the key from a id_ed25519.pub file on Client machine (Windows 11) to authorized_key on Server (Ubuntu)
    ```
    - Eventually you will be able to establish the ssh connection without providing a password like on the screen below:
    ![SSH_without_password](https://github.com/vitaliizghonnik/it-support-ticketing-lab/blob/main/Remote%20Access/screenshots/ssh_screenshots/4-ssh_without_pw.png)