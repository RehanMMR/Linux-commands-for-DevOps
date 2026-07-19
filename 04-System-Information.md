# 🖥️ System Information Commands

This section covers Linux commands used to retrieve system information, user details, and package management. These commands are useful for checking server details, verifying users, and managing software.

---

# uname

**Purpose:** Displays system information like the operating system and kernel version.

**Syntax**
```bash
uname [option]
```

**Example**
```bash
uname -a
```

**Output**
```text
Linux ubuntu 6.8.0-31-generic x86_64 GNU/Linux
```

**DevOps Use Case:** Verify the Linux kernel and OS version before installing software.

---

# uptime

**Purpose:** Shows how long the system has been running.

**Syntax**
```bash
uptime
```

**Example**
```bash
uptime
```

**Output**
```text
10:15:30 up 12 days, 4:32, 2 users, load average: 0.15, 0.20, 0.18
```

**DevOps Use Case:** Check server uptime after maintenance or deployments.

---

# date

**Purpose:** Displays the current system date and time.

**Syntax**
```bash
date
```

**Example**
```bash
date
```

**Output**
```text
Tue Jul 15 10:20:45 UTC 2025
```

**DevOps Use Case:** Verify system time while troubleshooting logs or scheduled jobs (Cron).

---

# who

**Purpose:** Shows users currently logged into the system.

**Syntax**
```bash
who
```

**Example**
```bash
who
```

**Output**
```text
ubuntu  pts/0  Jul 15 09:30
```

**DevOps Use Case:** Check who is currently connected to a production server.

---

# whoami

**Purpose:** Displays the current logged-in user.

**Syntax**
```bash
whoami
```

**Example**
```bash
whoami
```

**Output**
```text
ubuntu
```

**DevOps Use Case:** Confirm you're using the correct account before running administrative commands.

---

# which

**Purpose:** Shows the location of an executable command.

**Syntax**
```bash
which <command>
```

**Example**
```bash
which python3
```

**Output**
```text
/usr/bin/python3
```

**DevOps Use Case:** Verify whether a required tool is installed and where it is located.

---

# id

**Purpose:** Displays the current user's UID, GID, and group memberships.

**Syntax**
```bash
id
```

**Example**
```bash
id
```

**Output**
```text
uid=1000(ubuntu) gid=1000(ubuntu) groups=1000(ubuntu),27(sudo)
```

**DevOps Use Case:** Check if a user belongs to the required group before granting access.

---

# sudo

**Purpose:** Executes commands with administrator (root) privileges.

**Syntax**
```bash
sudo <command>
```

**Example**
```bash
sudo systemctl restart nginx
```

**Output**
```text
(Service restarted successfully)
```

**DevOps Use Case:** Restart services, install packages, or modify system configurations.

> 💡 Use `sudo` only when administrative privileges are required.

---

# apt

**Purpose:** Installs, updates, and removes software packages on Debian/Ubuntu systems.

**Syntax**
```bash
apt <command>
```

**Example**
```bash
sudo apt update
```

**Output**
```text
Package lists updated successfully.
```

**Another Example**
```bash
sudo apt install nginx
```

**DevOps Use Case:** Install required software like Docker, Git, Nginx, or Java on Linux servers.

> 💡 Common Commands:
>
> ```bash
> sudo apt update
> sudo apt upgrade
> sudo apt install <package>
> sudo apt remove <package>
> ```

---

## 🎯 Quick Revision Tips

- **uname -a** → System & kernel information
- **uptime** → Server uptime & load
- **date** → Current system date and time
- **who** → Logged-in users
- **whoami** → Current user
- **which** → Location of a command
- **id** → User and group information
- **sudo** → Run commands as administrator
- **apt** → Install and manage software packages

---

> 💡 **Interview Tip:** After SSH into a new Linux server, these are some of the first commands a DevOps Engineer usually runs:
>
> ```bash
> whoami
> uname -a
> uptime
> df -h
> free -h
> ```
>
> These commands quickly provide information about the user, operating system, server uptime, disk space, and memory.