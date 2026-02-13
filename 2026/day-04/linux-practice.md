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

<img width="918" height="210" alt="image" src="https://github.com/user-attachments/assets/6ae46c43-9751-46d6-886d-14f121f0b666" />


**What I Observed:**

- PID 1 is /sbin/init
- sshd is running

---
### Search for SSH Process
---

```bash
pgrep -a ssh
```

<img width="567" height="72" alt="image" src="https://github.com/user-attachments/assets/0ccfd83a-cd57-4138-b67b-d0655b382a0d" />


**What I Learned:**
 
- pgrep -a shows PID and command
- SSH daemon is active

---
### Service Checks
---
```bash
systemctl status ssh
```
<img width="837" height="251" alt="image" src="https://github.com/user-attachments/assets/bdc95aaf-9882-49c1-a09c-f27ca5360ff5" />


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

<img width="1005" height="575" alt="image" src="https://github.com/user-attachments/assets/f8f87139-9216-4444-97c3-ef5f750fb73c" />


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
<img width="985" height="310" alt="image" src="https://github.com/user-attachments/assets/f3d26075-e951-4cc1-8267-21ddb2445a16" />


**What i leaned**

- Service start time
- Service stop time
---
### Check System Logs
---

```bash
tail -n 20 /var/log/syslog
```
<img width="792" height="399" alt="image" src="https://github.com/user-attachments/assets/90b97a7a-ef90-4437-808c-7514339df519" />


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

```
<img width="1138" height="670" alt="image" src="https://github.com/user-attachments/assets/a1f8ef98-6371-4093-9554-8a42348620ab" />


 
```
What i learned from this task that ow to use basic Linux commands like ps,
systemctl, and journalctl to check running processes,
inspect services, and troubleshoot issues confidently. 
```
