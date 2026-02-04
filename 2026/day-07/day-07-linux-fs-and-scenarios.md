---
# Day 07 – Linux File System Hierarchy & Scenario-Based Practice
---

---
## Task
---

Today's goal is to understand where things live in Linux and practice troubleshooting like a DevOps engineer.

I created notes covering:

Linux File System Hierarchy (the most important directories)
Practice solving real-world scenarios step by step
This consolidates my Linux fundamentals and prepares you for real-world troubleshooting.
---
## Part 1: Linux File System Hierarchy
---

**Core Directory**
---
Core Directories (Must Know):

#### / (root) - The starting point of everything

>The Top of the entire Linux filesystem.
>Every file, direcotiry, and device exists user /.

**I would use this when…**

>I need to understand the overall structure of the Linux system.
---

#### /home - User home directories

>Personal directories for normal users (e.g., /home/altamash).

>Stores user files, documents, configs, and personal settings.

**I would use this when…**

>I want to store my own files or work as a normal user.

---
#### /root - Root user's home directory

> Personal home directory of the root (superuser).

**I would use this when…**

> I am logged in as root and need admin-level workspace.

---
### /etc - Configuration files

>System-wide configuration files for services and applications.Controls how the system behaves.

**I would use this when…**

> I need to configure a service, user, or system setting.
---
### /var/log - Log files (very important for DevOps!)

> Logs from system services, applications, and errors and Critical for troubleshooting.

**I would use this when…**

>I need to debug errors, monitor failures, or check security logs.
---
### /tmp - Temporary files

>Short-term files created by programs and it Usually cleared after reboot.

**I would use this when…**

I need a temporary storage location for scripts or downloads.
---
### /bin — Essential system binaries
>Basic commands required for system boot and recovery available to all users.

**I would use this when…**
>I need core Linux commands that must always work.
---
### /usr/bin — User binaries
>Most user-installed command-line programs and non-critical but cpmmpnly used tools.

**I would use this when…**

I run normal developer tools like Git, Python, Docker CLI, etc.
---
### /opt — Optional / Third-party apps

> Manually installed software (not from system package manager)

**I would use this when…**

> I install third-party applications or enterprise software.
---

---
## Hands-on task:
---
---
- find the largetst log file

```bash
sudo du -s /var/log/* | sort -h | tail -5
```
---
- Look at a config file in the /etc

```bash
cat /etc/hostname
```
---
- list home directory

```bash
ls -la
```
---
<iamge-1>
---
---

## Part 2: Scenario-Based Practice 
---
**Important:** Focus on understanding the troubleshooting flow, not memorizing commands.
---
### Scenario 1: Service Not Starting

```bash
A web application service called 'myapp' failed to start after a server reboot.
What commands would you run to diagnose the issue?
Write at least 4 commands in order.
```
---

---
```
step 1: sudo systemctl status myapp
# why: First i check my service applicaion is running or failed.

step 2: sudo systemctl is-enabled myapp
# why: Then i check that my service is enabled to start on boot.

step 3: sudo journalctl -u  myapp -n 50
# why: I'll check service logs in the real time 

step 4: sudo journal -b | grep -i myapp
# why: Check system logs around boot time

step 5: sudo systemctl restart myapp
# why: Try restarting the service manually

```
---

---
---
## 📝 Notes on journalctl Flags

### 🔹 The `-u` (Unit) Flag  
> Use this to filter logs by a specific systemd unit (usually a service).  
> It’s the fastest way to see why a specific application is failing without digging through the entire system log.

### 🔹 The `-b` (Boot) Flag  
> Use this to filter logs by a specific system boot session.  
> This is critical for diagnosing issues that happened before a reboot.
---
---

---
## Scenario 2: High CPU Usage
---
```
step 1: top or htop
# why: Overall CPU uages (It shows quick view) 

step 2: ps -eo pid,ppid,cmd,%cpu --sort=-%cpu | head
# why: Sort processes by CPU only

step 3: uptime
# why: Check system-wide load

```
---
---
## Scenario 3: Finding Service Logs

---
```
A developer asks: "Where are the logs for the 'docker' service?"
The service is managed by systemd.
What commands would you use?
```
---
---

```
step 1: journalctl -u docker.service -n 50
why: View last 50 lines of docker logs

step 2: journalctl -u docker.service -f
why:Follow logs in real-time (Live monitoring)

step 3: journalctl -u docker.service -b
why: View logs since last boot

```
---

Since Docker is a systemd service, I use journalctl -u docker.service with -n for recent logs and -f to stream them live.
---
---
From this task, I have learned how to check the status of a service and when it should be checked. I also learned how to monitor CPU utilization and where logs are located, including how to check logs in real time. Additionally, I realized that every problem has a solution — even when I already know the commands, real situations test my troubleshooting skills and how effectively I apply my knowledge.
---
