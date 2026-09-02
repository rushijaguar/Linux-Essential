<img width="1254" height="1254" alt="880f8ce1-60b3-40f5-861f-7a89f28ed220" src="https://github.com/user-attachments/assets/df230a3a-2639-4996-8d98-d0043b2ef864" />

## "Linux Essentials"

This repository contains practical Linux notes, commands, and examples for beginners and DevOps engineers.

## Topics Covered

- Linux file system
- Basic Linux commands
- File and directory management
- Users and groups
- File permissions
- Processes and services
- Package management
- Networking commands
- Disk and storage management
- Logs and troubleshooting
- Shell scripting
- SSH
- Git usage on Linux

## Common Commands

```bash
pwd
ls -la
cd /path/to/directory
mkdir directory-name
touch file.txt
cp source destination
mv source destination
rm file.txt
cat file.txt
```

## File Permissions

```bash
ls -l
chmod 755 script.sh
chown user:group file.txt
```

## Process and Service Management

```bash
ps -ef
top
systemctl status sshd
systemctl start sshd
systemctl enable sshd
journalctl -u sshd
```

## Package Management

### Amazon Linux

```bash
sudo dnf install package-name -y
sudo yum install package-name -y
```

### Ubuntu

```bash
sudo apt update
sudo apt install package-name -y
```

## Networking

```bash
ip addr
ip route
ping google.com
ss -tulnp
curl http://example.com
```

## Git Commands

```bash
git init
git status
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin <repository-url>
git push -u origin main
```

## Purpose

The goal of this repository is to maintain Linux learning notes and provide quick command references for system administration, DevOps, and cloud-infrastructure tasks.
