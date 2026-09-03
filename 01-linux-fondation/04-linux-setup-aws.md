<img width="1024" height="1536" alt="f5ee492a-99a1-4710-93a8-dbcd8f950fb3" src="https://github.com/user-attachments/assets/7680d314-502f-486f-97f7-909dcb51237f" />


# 🚀 Setup Linux Environment on AWS 🌥️


This guide explains how to set up a **Linux environment on AWS using Amazon EC2**.

## 📌 Prerequisites

Before starting, you need:

* An AWS Account
* Internet connection
* Basic knowledge of Linux commands
* An SSH client such as Terminal, PowerShell, or PuTTY

---

## 1️⃣ Create an AWS Account

Sign in to the **AWS Management Console**.

AWS provides cloud services that allow you to create and manage virtual servers.

---

## 2️⃣ Open EC2 Service

1. Log in to the AWS Console.
2. Search for **EC2**.
3. Open the **EC2 Dashboard**.

### Why EC2?

**Amazon EC2 (Elastic Compute Cloud)** provides virtual servers in the AWS cloud.

---

## 3️⃣ Launch an EC2 Instance

1. Click **Launch Instance**.
2. Enter a name for your server.
3. Example:

```text
Linux-DevOps-Server
```

An EC2 instance acts as a virtual Linux server.

---

## 4️⃣ Choose an Amazon Machine Image (AMI)

Select a Linux operating system.

Popular options include:

* Amazon Linux
* Ubuntu
* Red Hat Enterprise Linux
* Debian

For beginners, **Amazon Linux** or **Ubuntu** is recommended.

---

## 5️⃣ Select an Instance Type

Choose the required CPU and memory configuration.

Examples:

* `t2.micro`
* `t3.micro`

For basic learning and practice, a small instance type is usually sufficient.

---

## 6️⃣ Create a Key Pair

Create a new **Key Pair** and download the `.pem` file.

The key pair is used for secure SSH authentication.

Example:

```text
my-linux-key.pem
```

> ⚠️ Keep the `.pem` file secure. Do not share it publicly.

---

## 7️⃣ Configure Network Settings

Create or select a **Security Group**.

Allow the following inbound rule:

| Type | Protocol | Port |
| ---- | -------- | ---- |
| SSH  | TCP      | 22   |

SSH allows you to connect remotely to your Linux server.

---

## 8️⃣ Configure Storage

Select the required **Amazon EBS (Elastic Block Store)** volume.

You can configure:

* Volume size
* Volume type
* Encryption

Example:

```text
8 GB EBS Volume
```

---

## 9️⃣ Launch the Instance

Review all configurations:

* AMI
* Instance Type
* Key Pair
* Security Group
* Storage

Click **Launch Instance**.

Your Linux virtual machine will now start.

---

## 🔟 Connect to the Linux Server

After the instance is running, copy its **Public IPv4 address**.

### Amazon Linux

```bash
ssh -i my-linux-key.pem ec2-user@<public-ip>
```

### Ubuntu

```bash
ssh -i my-linux-key.pem ubuntu@<public-ip>
```

Example:

```bash
ssh -i my-linux-key.pem ec2-user@54.123.45.67
```

---

## 1️⃣1️⃣ Update the System

### Amazon Linux

```bash
sudo yum update -y
```

### Ubuntu

```bash
sudo apt update && sudo apt upgrade -y
```

This installs the latest available system updates and security patches.

---

## 1️⃣2️⃣ Install Required Tools

Install tools based on your requirements.

### Install Git

**Amazon Linux:**

```bash
sudo yum install git -y
```

**Ubuntu:**

```bash
sudo apt install git -y
```

### Install Docker

**Ubuntu:**

```bash
sudo apt install docker.io -y
```

### Install Nginx

**Ubuntu:**

```bash
sudo apt install nginx -y
```

---

## 1️⃣3️⃣ Verify the Environment

### Check Operating System

```bash
cat /etc/os-release
```

### Check Disk Space

```bash
df -h
```

### Check Memory

```bash
free -h
```

### Check IP Address

```bash
ip addr
```

### Check Installed Git Version

```bash
git --version
```

---

## 1️⃣4️⃣ Start Working

Your AWS Linux environment is now ready for:

* 🐧 Linux Administration
* 🔧 DevOps Practice
* 🐳 Docker
* 🔨 Jenkins
* ☸️ Kubernetes
* 🌐 Web Server Hosting
* ☁️ Cloud Projects

---

## 🏗️ Architecture

```text
Your Computer
      │
      │ SSH (Port 22)
      ▼
┌─────────────────────┐
│      AWS Cloud      │
│                     │
│  ┌───────────────┐  │
│  │   EC2 Server  │  │
│  │               │  │
│  │     Linux     │  │
│  │               │  │
│  │ Git | Docker  │  │
│  │ Jenkins | etc │  │
│  └───────────────┘  │
└─────────────────────┘
```

---

## 📚 Summary

| Step | Action                   |
| ---- | ------------------------ |
| 1    | Create AWS Account       |
| 2    | Open EC2 Service         |
| 3    | Launch EC2 Instance      |
| 4    | Select Linux AMI         |
| 5    | Choose Instance Type     |
| 6    | Create Key Pair          |
| 7    | Configure Security Group |
| 8    | Configure EBS Storage    |
| 9    | Launch Instance          |
| 10   | Connect using SSH        |
| 11   | Update Linux             |
| 12   | Install Required Tools   |
| 13   | Verify Environment       |
| 14   | Start Working            |

---

## 🎯 Conclusion

Amazon EC2 makes it easy to create a **Linux server in the cloud** without purchasing physical hardware. You can use this environment to learn **Linux, AWS, DevOps, Docker, Jenkins, and Kubernetes**.

**Happy Learning! 🚀**
