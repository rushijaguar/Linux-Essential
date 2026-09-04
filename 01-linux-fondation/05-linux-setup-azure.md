<img width="1024" height="1536" alt="c850f403-199a-4c62-b3f7-e392f36b4e04" src="https://github.com/user-attachments/assets/75a9e6e3-59f0-43ba-a42f-32d1346218f3" />
//////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

# 🚀 Setup Linux Environment on Microsoft Azure 💻

A beginner-friendly, step-by-step guide to launch and configure a Linux Virtual Machine (VM) on Azure.

---

## 📋 Table of Contents

1. [Prerequisites](#-prerequisites)
2. [What is an Azure Virtual Machine?](#-what-is-an-azure-virtual-machine)
3. [Architecture Overview](#-architecture-overview)
4. [Step 1: Create an Azure Account](#-step-1-create-an-azure-account)
5. [Step 2: Open Azure Portal](#-step-2-open-azure-portal)
6. [Step 3: Create a Linux Virtual Machine](#-step-3-create-a-linux-virtual-machine)
7. [Step 4: Configure Basic Settings](#-step-4-configure-basic-settings)
8. [Step 5: Configure Networking](#-step-5-configure-networking)
9. [Step 6: Review and Create](#-step-6-review-and-create)
10. [Step 7: Connect to the Linux VM](#-step-7-connect-to-the-linux-vm)
11. [Step 8: Initial Linux Configuration](#-step-8-initial-linux-configuration)
12. [Step 9: Install Useful Tools](#-step-9-install-useful-tools)
13. [Step 10: Test a Web Server](#-step-10-test-a-web-server)
14. [Important Linux Commands](#-important-linux-commands)
15. [Stop or Delete the VM](#-stop-or-delete-the-vm)
16. [Troubleshooting](#-troubleshooting)

---

# 📌 Prerequisites

Before starting, you need:

* A Microsoft Azure account
* Internet connection
* Basic understanding of Linux commands
* An SSH client

### For Windows Users

You can use:

* Windows Terminal
* PowerShell
* Command Prompt
* PuTTY

Modern versions of Windows also support SSH directly from PowerShell or Windows Terminal.

---

# 🌥️ What is an Azure Virtual Machine? 🧑🏻‍💻

An **Azure Virtual Machine (VM)** is a virtual computer running in Microsoft Azure's cloud.

Instead of purchasing a physical server, you can create a virtual server with:

* CPU
* RAM
* Storage
* Network
* Operating System

For this tutorial, we will create a Linux VM.

### Example

```text
Your Laptop
     |
     | SSH Connection
     |
     v
+----------------------+
|     Azure Cloud      |
|                      |
|   Linux Virtual VM   |
|                      |
|   Ubuntu Server      |
+----------------------+
```

---

# 🏗️ Architecture Overview

When you create a Linux VM, Azure automatically connects several resources.

```text
                    Internet
                        |
                        v
                Public IP Address
                        |
                        v
              +-------------------+
              | Network Security  |
              | Group (NSG)       |
              +-------------------+
                        |
                        v
                Virtual Network
                     (VNet)
                        |
                        v
                     Subnet
                        |
                        v
              +-------------------+
              |    Linux VM       |
              |                   |
              | Ubuntu / Linux    |
              +-------------------+
                        |
                        v
                  Managed Disk
```

---

# 📝 Step 1: Create an Azure Account

1. Open the Azure website.
2. Sign in with your Microsoft account.
3. Complete account verification.
4. Open the Azure Portal.

After logging in, you will see the Azure dashboard.

---

# 🖥️ Step 2: Open Azure Portal

From the Azure Portal:

1. Search for **Virtual Machines**
2. Click **Virtual Machines**
3. Click **Create**
4. Select **Azure virtual machine**

You are now ready to create a Linux server.

---

# 🚀 Step 3: Create a Linux Virtual Machine

You will see several configuration sections.

The most important sections are:

```text
1. Basics
2. Disks
3. Networking
4. Management
5. Monitoring
6. Advanced
7. Tags
8. Review + Create
```

For beginners, focus mainly on:

* Basics
* Disks
* Networking

---

# ⚙️ Step 4: Configure Basic Settings

## 4.1 Select Subscription

Choose your Azure subscription.

```text
Subscription
    |
    └── Azure Subscription
```

---

## 4.2 Create a Resource Group

A **Resource Group** is a container used to organize Azure resources.

### Example

```text
Resource Group:

linux-rg
```

A resource group can contain:

```text
linux-rg
│
├── Virtual Machine
├── Public IP
├── Network Interface
├── Network Security Group
└── Managed Disk
```

### Create a new Resource Group

Click:

```text
Create new
```

Enter:

```text
linux-rg
```

Then click:

```text
OK
```

---

# 🌍 4.3 Select Region

Choose a region close to your users or location.

Example:

```text
Central India
```

Other examples:

```text
East US
West Europe
Southeast Asia
```

### Important

Choosing a nearby region can help reduce network latency.

---

# 🐧 4.4 Select the Linux Image

Under **Image**, select a Linux operating system.

Recommended for beginners:

```text
Ubuntu Server LTS
```

Ubuntu is popular because:

* Beginner-friendly
* Large community support
* Frequently used in cloud environments
* Good documentation

---

# 💻 4.5 Select VM Size

The VM size determines:

* CPU
* RAM
* Performance
* Cost

For learning purposes, choose a small VM size available in your subscription.

Example:

```text
Size: Standard_B2s
```

This is suitable for basic learning and testing.

### Remember

Larger VM sizes usually provide more:

```text
CPU
RAM
Performance
```

But they can also cost more.

---

# 👤 4.6 Configure Administrator Account

Choose:

```text
Authentication type: SSH public key
```

This is generally recommended for secure Linux administration.

### Username Example

```text
azureuser
```

Azure can generate an SSH key pair, or you can use an existing SSH public key.

### Example

```text
Username: azureuser

Authentication:
SSH Public Key
```

---

# 🌐 Step 5: Configure Networking

Networking allows you to connect to the Linux VM.

Azure provides options such as:

* Virtual Network (VNet)
* Subnet
* Public IP
* Network Security Group (NSG)

---

## 5.1 Virtual Network

A **Virtual Network (VNet)** is your private network inside Azure.

Example:

```text
VNet Name:

linux-vnet
```

---

## 5.2 Subnet

A subnet divides a network into smaller networks.

Example:

```text
Subnet:

default
```

Architecture:

```text
VNet
│
└── Subnet
      │
      └── Linux VM
```

---

## 5.3 Public IP

A Public IP allows you to connect to the VM from the internet.

Example:

```text
Public IP

20.xxx.xxx.xxx
```

Your actual IP address will be different.

---

## 5.4 Network Security Group (NSG)

An **NSG acts like a firewall** for Azure resources.

For SSH access, allow:

```text
Port: 22
Protocol: TCP
Purpose: SSH
```

Rule:

```text
Source: Your IP address
Destination Port: 22
Protocol: TCP
Action: Allow
```

### Security Tip

For better security, avoid allowing SSH access from everywhere when possible.

Prefer:

```text
Source: My IP
```

Instead of:

```text
Source: Any
```

---

# ✅ Step 6: Review and Create

After completing the configuration:

1. Click **Review + create**
2. Azure validates the configuration
3. Fix any validation errors
4. Click **Create**

Azure will now deploy your VM.

Deployment may take a few minutes.

---

# 🔑 Step 7: Connect to the Linux VM

After deployment:

1. Go to **Virtual Machines**
2. Select your VM
3. Click **Connect**
4. Select **SSH**

Azure will show you the SSH connection details.

---

## Connect from Windows Terminal or PowerShell

The command will look similar to:

```bash
ssh azureuser@PUBLIC_IP_ADDRESS
```

Example:

```bash
ssh azureuser@20.123.45.67
```

Replace:

```text
azureuser
```

with your VM username.

Replace:

```text
20.123.45.67
```

with your VM's Public IP address.

---

## If Using a Private Key

Make sure you use the correct private key.

Example:

```bash
ssh -i ~/.ssh/azure_key.pem azureuser@20.123.45.67
```

The exact key location depends on where you saved it.

---

# 🎉 Step 8: Initial Linux Configuration

After successfully connecting:

You will see something similar to:

```text
Welcome to Ubuntu
```

You are now inside your Azure Linux VM.

---

## Check Current User

```bash
whoami
```

Example output:

```text
azureuser
```

---

## Check Operating System

```bash
cat /etc/os-release
```

---

## Check Kernel Version

```bash
uname -r
```

---

## Check Hostname

```bash
hostname
```

---

## Check IP Address

```bash
ip addr
```

or:

```bash
hostname -I
```

---

# 🔄 Update the System

Before installing software, update the package information.

For Ubuntu:

```bash
sudo apt update
```

Upgrade installed packages:

```bash
sudo apt upgrade -y
```

---

# 📦 Step 9: Install Useful Tools

## Install Git

```bash
sudo apt install git -y
```

Check version:

```bash
git --version
```

---

## Install Curl

```bash
sudo apt install curl -y
```

Check:

```bash
curl --version
```

---

## Install Wget

```bash
sudo apt install wget -y
```

---

## Install Tree

```bash
sudo apt install tree -y
```

Example:

```bash
tree
```

---

## Install Vim

```bash
sudo apt install vim -y
```

---

# 🌐 Step 10: Test a Web Server

Let's install **Nginx**.

## Install Nginx

```bash
sudo apt install nginx -y
```

---

## Check Nginx Status

```bash
sudo systemctl status nginx
```

You should see:

```text
active (running)
```

---

## Enable Nginx

This ensures Nginx starts automatically after reboot.

```bash
sudo systemctl enable nginx
```

---

## Open HTTP Port

To access the website from the browser, allow:

```text
Port: 80
Protocol: TCP
```

In Azure:

```text
Virtual Machine
      |
      v
Networking
      |
      v
Add Inbound Port Rule
```

Configure:

```text
Source: Any
Source Port Range: *
Destination: Any
Service: HTTP
Destination Port: 80
Protocol: TCP
Action: Allow
```

Save the rule.

---

## Access the Website

Open your browser and enter:

```text
http://PUBLIC_IP_ADDRESS
```

Example:

```text
http://20.123.45.67
```

You should see the Nginx welcome page.

---

# 📝 Create a Simple HTML Website

Go to the Nginx web directory:

```bash
cd /var/www/html
```

Edit the default page:

```bash
sudo nano index.html
```

Add:

```html
<!DOCTYPE html>
<html>
<head>
    <title>My Azure Linux Server</title>
</head>

<body>
    <h1>Hello from Azure Linux VM!</h1>
    <p>Nginx is running successfully.</p>
</body>
</html>
```

Save the file.

Now refresh your browser:

```text
http://PUBLIC_IP_ADDRESS
```

You should see your custom webpage.

---

# 🛠️ Important Linux Commands

## Check Current Directory

```bash
pwd
```

---

## List Files

```bash
ls
```

Detailed list:

```bash
ls -l
```

Show hidden files:

```bash
ls -la
```

---

## Change Directory

```bash
cd /home
```

Go back:

```bash
cd ..
```

Go to home directory:

```bash
cd ~
```

---

## Create a Directory

```bash
mkdir project
```

---

## Create a File

```bash
touch file.txt
```

---

## View File Content

```bash
cat file.txt
```

---

## Copy Files

```bash
cp file.txt backup.txt
```

---

## Move Files

```bash
mv file.txt project/
```

---

## Remove Files

```bash
rm file.txt
```

---

## Check Disk Usage

```bash
df -h
```

---

## Check Memory Usage

```bash
free -h
```

---

## Check Running Processes

```bash
ps aux
```

---

## Check System Uptime

```bash
uptime
```

---

# 🔐 Basic Security Practices

When working with Linux VMs in Azure:

### 1. Use SSH Keys

Prefer:

```text
SSH Public Key
```

over password authentication when possible.

---

### 2. Restrict SSH Access

Avoid:

```text
SSH from Anywhere
0.0.0.0/0
```

Prefer allowing access only from trusted IP addresses.

---

### 3. Keep the System Updated

Regularly run:

```bash
sudo apt update
sudo apt upgrade -y
```

---

### 4. Do Not Run Everything as Root

Use:

```bash
sudo
```

only when administrative privileges are required.

---

### 5. Stop Unused VMs

If you are not using a VM, stop or deallocate it to avoid unnecessary compute charges.

---

# 💰 Step 11: Stop or Delete the VM

## Stop the VM

From Azure Portal:

```text
Virtual Machines
       |
       v
Select VM
       |
       v
Stop
```

For cloud cost management, check whether the VM is fully stopped/deallocated.

---

## Delete the VM

If you no longer need the environment:

```text
Virtual Machines
       |
       v
Select VM
       |
       v
Delete
```

You can also delete the entire resource group.

### Delete Resource Group

```text
Resource Groups
       |
       v
linux-rg
       |
       v
Delete Resource Group
```

This removes the resources inside that resource group.

⚠️ **Warning:** Deleting a resource group can permanently delete all resources inside it.

---

# 🛠️ Troubleshooting

## Problem 1: Unable to Connect Using SSH

Check:

### Is the VM Running?

```text
Virtual Machines
    |
    └── Check Status
```

---

### Is Port 22 Allowed?

Check the Network Security Group.

Make sure:

```text
Port: 22
Protocol: TCP
Action: Allow
```

---

### Are You Using the Correct Public IP?

Check:

```text
Virtual Machine
    |
    └── Overview
           |
           └── Public IP Address
```

---

## Problem 2: Website Is Not Opening

Check Nginx:

```bash
sudo systemctl status nginx
```

Restart Nginx:

```bash
sudo systemctl restart nginx
```

---

Check whether port 80 is listening:

```bash
sudo ss -tulnp
```

---

Check Azure NSG inbound rules.

Make sure HTTP port:

```text
80
```

is allowed.

---

# 📊 Quick Command Cheat Sheet

| Task             | Command                            |
| ---------------- | ---------------------------------- |
| Check user       | `whoami`                           |
| Check OS         | `cat /etc/os-release`              |
| Check hostname   | `hostname`                         |
| Check IP         | `ip addr`                          |
| Update packages  | `sudo apt update`                  |
| Upgrade packages | `sudo apt upgrade -y`              |
| Check disk       | `df -h`                            |
| Check memory     | `free -h`                          |
| Check processes  | `ps aux`                           |
| Check uptime     | `uptime`                           |
| Install package  | `sudo apt install <package> -y`    |
| Check service    | `sudo systemctl status <service>`  |
| Restart service  | `sudo systemctl restart <service>` |

---

# 🎯 Complete Workflow

```text
Create Azure Account
        |
        v
Open Azure Portal
        |
        v
Create Resource Group
        |
        v
Create Linux VM
        |
        v
Select Ubuntu Image
        |
        v
Configure VM Size
        |
        v
Configure SSH Authentication
        |
        v
Configure Networking
        |
        v
Create VM
        |
        v
Connect Using SSH
        |
        v
Update Linux System
        |
        v
Install Required Tools
        |
        v
Configure Nginx
        |
        v
Deploy Application
```

---

# 🧪 Beginner Practice Tasks

After creating your VM, practice the following:

### Task 1

Check your Linux version:

```bash
cat /etc/os-release
```

---

### Task 2

Create a directory:

```bash
mkdir devops-practice
```

---

### Task 3

Create a file:

```bash
touch devops.txt
```

---

### Task 4

Install Git:

```bash
sudo apt install git -y
```

---

### Task 5

Install Nginx:

```bash
sudo apt install nginx -y
```

---

### Task 6

Create a simple website:

```bash
sudo nano /var/www/html/index.html
```

---

# 🎓 What You Learned

After completing this guide, you should understand:

* ✅ What an Azure Virtual Machine is
* ✅ How to create a Resource Group
* ✅ How to launch a Linux VM
* ✅ How to select an Ubuntu image
* ✅ How to configure networking
* ✅ What a Virtual Network (VNet) is
* ✅ What a Network Security Group (NSG) is
* ✅ How to connect using SSH
* ✅ How to update Linux packages
* ✅ How to install software
* ✅ How to install Nginx
* ✅ How to host a basic website
* ✅ Basic Linux administration commands

---

# 🚀 Next Steps

After learning how to create a Linux VM, continue with:

```text
Linux Fundamentals
       ↓
Linux Networking
       ↓
Shell Scripting
       ↓
Git & GitHub
       ↓
Docker
       ↓
Jenkins
       ↓
Kubernetes
       ↓
Terraform
       ↓
Ansible
       ↓
Azure DevOps
```

---

# 👨‍💻 Author

**DevOps & Cloud Learning Project**

---

## ⭐ Happy Learning!

> **Practice is the best way to learn Linux and Cloud. Create a VM, experiment with it, break things safely, troubleshoot them, and learn from the process.**
