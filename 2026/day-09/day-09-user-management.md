# DAY-09 — DevOps Challenge Summary
---

---

**In this challenge, I learned:** 
---
- How to create a user in Linux

- How to create a group

- Difference between useradd and adduser

- How to add a user to a group

- How to check and modify user permissions

- How to check and modify group permissions


- Some useful commands for user and group interaction.

- what is the diffrence between primary and secondry Group.
---

## Key Concepts Practiced:
- Usefull Commands.

- User management in Linux

- Group management in Linux

- File and directory permission handling

- Understanding ownership and access control

---

---
### **DAY-09 — Useful Linux Commands (User & Group Management)**
---

| Sl No | Command                           | Purpose                                                |
| ----- | --------------------------------- | ------------------------------------------------------ |
| 1     | `sudo useradd devuser`            | Low-level command to create user (minimal setup)       |
| 2     | `sudo adduser devuser`            | Interactive command to create user with home & details |
| 3     | `sudo useradd -m devuser`         | Create user with home directory                        |
| 4     | `sudo passwd devuser`             | Set password for user                                  |
| 5     | `sudo groupadd devops`            | Create a new group                                     |
| 6     | `sudo usermod -aG devops devuser` | Add user to group                                      |
| 7     | `newgrp devops`                   | Switch to another group in current session             |
| 8     | `id devuser`                      | Check user details                                     |
| 9     | `cat /etc/passwd`                 | List all users                                         |
| 10    | `cat /etc/group`                  | List all groups                                        |
| 11    | `whoami`                          | Show current user                                      |
| 12    | `ls -l file.txt`                  | Check file owner & permission                          |
| 13    | `sudo chown devuser file.txt`     | Change file owner                                      |
| 14    | `sudo chown :devops file.txt`     | Change file group                                      |
| 15    | `chmod 700 file.txt`              | Owner full access only                                 |
| 16    | `chmod 444 file.txt`              | Read-only for all                                      |
| 17    | `chmod 777 file.txt`              | Full access for all (not recommended)                  |
| 18    | `sudo userdel devuser`            | Delete a user                                          |
| 19    | `sudo groupdel devops`            | Delete a group                                         |
| 20  | `sudo passwd <username>`  | Set password for User | 
| 21 | `newgrp <group name>` | To refresh the group directory to update group |
| 21 | ` getent passwd $USER` | to check user group
---

*** Difference between useradd and adduser: ***

- useradd → System-level command, requires manual configuration.

- adduser → Interactive script, automatically creates home, shell, etc.

---

---
## **Challenge Tasks**
---

## Task 1: Create Users
---

-- Created three users with home directory and password

*** commands ***


### USER CREATION

```bash
sudo useradd tokyo
sudo useradd berlin
sudo useradd professor
```
---

### Verify Group creation

```bash
sudo cat /etc/group | tail -n 5
```
---

### PASSWORD SETUP

```bash
sudo passwd tokyo
sudo passwd berlin
sudo passwd professor

```
---

<img width="691" height="375" alt="Screenshot 2026-02-02 191644" src="https://github.com/user-attachments/assets/959ccc84-0041-4ffd-9624-69864bf6884d" />

---

## Task 2: Create Groups (10 minutes)
 
 - Created two groups:

*** commands ***
### New Group Add

```bash
sudo groupadd <groupname>
sudo groupadd <groupname>
```

### Verify Group creation

```bash
sudo cat /etc/group | tail -n 5
```

---

<img width="669" height="154" alt="Screenshot 2026-02-02 192507" src="https://github.com/user-attachments/assets/690b1c7f-d423-4d7c-9e49-9441a4dfd7e0" />

---

## Task 3: Assign to Groups
 ---
 Assign users:
 ---

- tokyo → developers

```bash
sudo usermod -aG developers tokyo
```

- berlin → developers + admins (both groups)

```bash
sudo usermod -aG developers berlin
sudo usermod -aG admins berlin
```

- professor → admins

```bash
sudo usermod -aG admins professor
```
---

<img width="1086" height="253" alt="Screenshot 2026-02-02 204332" src="https://github.com/user-attachments/assets/96e93c63-13fe-432c-bdb9-9d4dddf7cdd0" />

---

## Task 4: Shared Directory

---
- 1. Create directory: /opt/dev-project

```bash
sudo -p /opt/dev-project
cd /opt
```
---

---
- 2. Set group owner to developers

```bash
sudo chgrp <groupname> <path of directory>
```
---

---
- 3. Set permissions to 775 (rwxrwxr-x)

```bash
sudo chmod 775 
```
---

---
- 4. Test by creating files as tokyo and berlin

```bash

## Switch User tokyo
su berlin
## create test file on user tokyo
touch /opt/dev-project/berlin-test.txt


## Switch User tokyo
su tokyo
## create test file on user tokyo
touch /opt/dev-project/tokyo-test.txt

```
---

<img width="1182" height="656" alt="Screenshot 2026-02-02 205142" src="https://github.com/user-attachments/assets/2cacfcd4-0d62-451e-8fac-b23d5dfa2edd" />


## Task 5: Team Workspace 

- **Create user nairobi with home directory**

```bash
sudo useradd nairobi
```

- **Create group project-team**

```bash
sudo groupadd project-team
```

- Add nairobi and tokyo to project-team

```bash 
sudo usermod -aG project-team tokyo 
sudo usermod -aG project-team nairobi
```

- Create /opt/team-workspace directory

```bash 
mkdir -p /opt/team-workspace
```
- Set group to project-team, permissions to 775

```bash
sudo chmod 775 team-workspace
ls -ld /opt/team-workspace
```
---
- Test by creating file as nairobi
---

  <img width="828" height="374" alt="Screenshot 2026-02-02 221656" src="https://github.com/user-attachments/assets/638920b5-7873-4dd4-9076-9582dfc96e10" />


<img width="1108" height="211" alt="Screenshot 2026-02-02 210910" src="https://github.com/user-attachments/assets/bc15d33d-fb9f-41c1-ad7f-cd4cdbfea57d" />

