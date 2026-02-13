---
# Day 04 – Linux Practice: Processes and Services
---

---
## Process Checks
---
- List Running Processes

```bash
ps aux | head -10
```
<image-1>

**What I Observed:**

- PID 1 is /sbin/init
- sshd is running

---
### Search for SSH Process
---

```bash
pgrep -a ssh
```
<image-2>

**What I Learned:**
 
- pgrep -a shows PID and command
- SSH daemon is active

---
### Service Checks
---
```bash
systemctl status ssh
```
<image-4>

**Observation:***

- Service is enabled
- Service is running
- No recent failures

---
### List Active Services
---

```bash
systemctl list-units --type=service --state=running
```
**What I Learned:***

- Only running services are shown
- Good way to quickly inspect system health
 
---
## Log Checks
---
## Check SSH Logs

```bash
sudo journalctl -u nginx | tail -10
```
<image>

**What i leaned**

- Service start time
- Service stop time
---
### Check System Logs
---

```bash
tail -n 20 /var/log/syslog
```
<image>

**What I Learned:**

- tail is useful for quick log inspection
- Logs help verify background tasks
---

---
## Mini Troubleshooting Flow
---
*** Scenario: NGINX not working ***

Steps I would take:

- 1. Check if process is running
```bash
 pgrep -a nginx
 ```
- 2. Check service status:
```bash
sudo systemctl status nginx
```
- 3. if not running:

```bash
sudo systemctl restart nginx
```

4.Check logs:
```bash
journalctl -u nginx --since "10 minutes ago" 
<final image>

> What i learned from this task that ow to use basic Linux commands like ps, systemctl, and journalctl to check running processes, inspect services, and troubleshoot issues confidently. <
