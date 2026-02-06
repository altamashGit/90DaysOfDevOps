---
# Day 05 – Linux Troubleshooting Drill: CPU, Memory, and Logs
---
---
## Task
---
 
Today’s goal is to run a focused troubleshooting drill.

I will pick a running process/service on my system and:

- Capture a quick health snapshot (CPU, memory, disk, network)
- Trace logs for that service
- Write a mini runbook describing what you did and what you’d do next if things 
were worse

This turns yesterday’s practice into a repeatable troubleshooting routine.

---
---
## 🎯 Target service / process

Service chosen: **ssh (sshd)**  
Reason: It is critical for remote access and always running on my system.

---
---
### Environment basics
---
- 1. It shows karnel version and architecture and normal (64-bit Linux)

```bash
uname -a
````

- 2. Here server is running stable, supported Linux distribution

```bash
cat /etc/os-release
```
---
###Filesystem sanity
---

-  1. **Runbook file created**

```bash
mkdir /tmp/runbook-demo
```
- 2 Copy host file content into tmp directory

```bash
cp /etc/hosts /tmp/runbook-demo/hosts-copy
```

- 3 Cheking file permissions.
**Observation:** Filesystem is writable; permissions look normal
```bash
ls -l /tmp/runbook-demo
```
### CPU & Memory Snapshot

- 1. Check SSH process CPU & memory.

**Observation:** sshd is using minimal CPU and memory.

```bash
ps -o pid,pcpu,pmem,comm -C sshd | head
```
- 3. Memory Check
**Observation:** Plenty of free RAM; no swap usage.

```bash
free -h
```

```
NOTE: 
what is swap:
Swap usage is the amount of disk space your system is using as extra memory when your RAM (physical memory) is full.
```


## Disk & IO Snapshot

- 1. Filesystem size and disk utilization

**Observation:** Disk is healthy; not close to full.

```bash
df -h
```
 - 2. Check log size
 **Observation:** Logs are not unusually large. 

```bash
du -sh /var/log
```

## Network Snapshot
 
- 1. Check listening ports
 
 **Observation:** SSH is listening correctly on port 22.
 
 ```bash
 ss -tulpn | grep ssh
 ```

 - 2. Test connectivity
 
 **Observation:** Network connectivity is healthy.

 ```
 ping -c 3 8.8.8.8
 ```

 ## Logs

- 1. Recent logs check  
 **Observation:** No recent authentication failures or errors.

```bash
journalctl -u ssh --no-pager -n 50
```
- 2. System log tail

**Observation:** Normal login activity; no suspicious attempts.

```bash
tail -n 50 /var/log/auth.log
```

---

---
## 🔍 Quick Findings

- SSH service is running normally  
- CPU and memory usage are low  
- Disk space is healthy  
- Network connectivity is stable  
- No alarming errors in logs  

👉 **Overall system status: HEALTHY ✅**
---
