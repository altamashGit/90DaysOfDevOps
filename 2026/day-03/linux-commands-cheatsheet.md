---
# Linux Commands Cheatsheet
---
---
## File & Directory Commands
---

## 📂 File & Directory Commands

| Command                     | Use Case                                   |
|-----------------------------|--------------------------------------------|
| `pwd`                       | Show current directory                     |
| `ls -la`                    | List all files (including hidden)          |
| `cd <dir>`                  | Change directory                           |
| `mkdir <dir>`               | Create directory                           |
| `rm -rf <dir/file>`         | Remove file or directory                   |
| `cp <src> <dest>`           | Copy file                                  |
| `mv <src> <dest>`           | Move or rename                             |
| `find . -name "file.txt"`   | Search for a file by name                  |

---

## 📄 File Viewing & Editing

| Command                | Use Case                          |
|------------------------|-----------------------------------|
| `cat file.txt`         | Display file content              |
| `less file.txt`        | View large file                   |
| `head -n 20 file.txt`  | Show first 20 lines               |
| `tail -n 20 file.txt`  | Show last 20 lines                |
| `tail -f file.txt`     | Monitor file in real time         |
| `nano file.txt`        | Edit file                         |

---

## 🔍 Process Management

| Command            | Use Case                              |
|--------------------|----------------------------------------|
| `ps aux`           | List running processes                 |
| `top`              | Real-time process monitor              |
| `htop`             | Enhanced process monitor               |
| `pgrep nginx`      | Find process by name                   |
| `kill <PID>`       | Terminate process                      |
| `kill -9 <PID>`    | Force kill process                     |

---

## ⚙️ Service Management (systemd)

| Command                                      | Use Case                        |
|----------------------------------------------|---------------------------------|
| `systemctl status nginx`                     | Check service status            |
| `systemctl start nginx`                      | Start service                   |
| `systemctl stop nginx`                       | Stop service                    |
| `systemctl restart nginx`                    | Restart service                 |
| `systemctl enable nginx`                     | Enable service at boot          |
| `systemctl list-units --type=service`        | List active services            |

---

## 📜 Logs & Debugging

| Command                          | Use Case                          |
|----------------------------------|-----------------------------------|
| `journalctl -u nginx`            | View service logs                 |
| `journalctl -xe`                 | View system errors                |
| `tail -f /var/log/syslog`        | Monitor system logs               |
| `dmesg | tail`                   | View recent kernel logs           |

---

## 🌐 Networking

| Command            | Use Case                          |
|--------------------|-----------------------------------|
| `ip a`             | Show IP address                   |
| `ping google.com`  | Test network connectivity         |
| `curl ifconfig.me` | Show public IP                    |
| `netstat -tulnp`   | Check open ports                  |
| `ss -tulnp`        | Modern netstat alternative        |

---

## 👤 User & Permissions

| Command                 | Use Case                         |
|-------------------------|----------------------------------|
| `whoami`                | Show current user                |
| `id`                    | Display user ID information      |
| `sudo <command>`        | Run command as root              |
| `chmod 755 file.sh`     | Change file permissions          |
| `chown user:group file` | Change file ownership            |

---

## 🐙 Git Commands

| Command                          | Use Case                          |
|----------------------------------|-----------------------------------|
| `git clone <repo>`               | Clone repository                  |
| `git status`                     | Check repo status                 |
| `git add .`                      | Stage all changes                 |
| `git commit -m "message"`        | Commit changes                    |
| `git push`                       | Push to remote repo               |
| `git pull`                       | Pull latest changes               |
| `git branch`                     | List branches                     |
| `git checkout -b feature`        | Create and switch branch          |
