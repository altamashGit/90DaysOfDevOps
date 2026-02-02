---
# Day 08 – Cloud Server Setup: Docker, Nginx & Web Deployment
---

---
Commands Used
---

| Si. No.   | Category | Purpose | Command |
|--- |----------|---------|---------|
| 1. | SSH | Connect to AWS server | `ssh -i your-key.pem ubuntu@<your-instance-ip>` |
| 2. | Service Management | Check Nginx status | `sudo systemctl status nginx` |
| 3.| Logs | View last 5 lines | `sudo tail -n 50 /var/log/nginx/access.log` |
| 4. | Logs | View first 10 lines | `sudo head -n 20 /var/log/nginx/access.log` |
| 5. | Pipeline | Filter successful requests | `sudo tail -n 10 /var/log/nginx/access.log \| grep "200"` |
| 6. | Pipeline | Show first 10 successful requests | `sudo cat /var/log/nginx/access.log \| grep "200" \| head -n 10` |
| 7. | Redirection | Save logs to file | `sudo cat /var/log/nginx/access.log > ~/nginx-logs.txt` |
| 8. | Redirection | Append new logs | `sudo tail -n 100 /var/log/nginx/access.log >> ~/nginx-logs.txt` |
| 9. | File Check | List file details | `ls -lh ~/nginx-logs.txt` |
| 10. | File Check | Preview saved file | `head -n 20 ~/nginx-logs.txt` |
| 11. | SCP (AWS) | Download logs locally | `scp -i your-key.pem ubuntu@<your-instance-ip>:~/nginx-logs.txt .` |
| 12. | Verify Nginx Install | `sudo systemctl status nginx` |
| 13. | View Nginx Logs (LIVE) | `sudo tail -f /var/log/nginx/access.log
` |

---
## Part 1: Launch Cloud Instance & SSH Access
- Step 1: Create a Cloud Instance

<image 1>

- Step 2: Connect via SSH

<image 2>

---
## Part 2: Install Docker
---

- Step 1: Update System

```bash
sudo apt update -y
```

- Step 3: Install Nginx

```bash
sudo apt install nginx
```

- step 4: Verify Nginx is running:

```bash
sudo systamctl status nginx
```
---

<image 3>
---

---
## Part 3: Security Group Configuration
---

Test Web Access: Open browser and visit: 

```bash
http://<your-instance-ip>
```

You should see the Nginx welcome page!

<nginx web server>

## Part 4: Extract Nginx Logs

- Step 1: View Nginx Logs

**Live Logs**

```bash
sudo tail -f /var/log/nginx/access.log
```

```bash
sudo tail n 5 /var/log/nginx/access.log
```

- Step 2: Save Logs to File

 
 **check that the file exists**

```bash
ls -lh ~/nginx-logs.txt
```
 
 **Redirect and save log file to the log.txt**

```bash
sudo cat /var/log/nginx/access.log > ~/nginx-logs.txt
```
- Step 3: Download Log File to Your Local Machine

<image 4>

**(Ubuntu User)**

```bash
scp -i your-key.pem ubuntu@<your-instance-ip>:~/nginx-logs.txt .
```
<image local copy>

---
You can also open it:
---
```bash
cat nginx-logs.txt | head
```
<image 4>


## What I Learned
 - To after installing any services first check status of the service then start or enable it.

 - While running nginx server you must allow inbound rule on port 80 and the appropriate source mosty for learning pupose most people use anywere which is not good.

 - In the Logs section, I learned how web server logs work, how to monitor them in real time, how to filter and save them using Linux tools, and how to securely transfer log files from a remote cloud server to my local machine using SCP.

 - How to read real web logs
     - By viewing /var/log/nginx/access.log i saw:---

      - Visitor IP address
      - Request type (GET, POST)
      - Time of request
      - HTTP status codes (200, 404, etc.)
