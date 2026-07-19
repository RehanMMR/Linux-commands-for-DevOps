# 🚀 Pro Linux Commands

This section covers powerful text-processing commands that are used daily by DevOps Engineers for log analysis, automation, configuration management, and troubleshooting.

---

# grep

**Purpose:** Searches for a specific text or pattern in a file or command output.

**Syntax**
```bash
grep [options] "pattern" <file>
```

**Example**
```bash
grep "ERROR" app.log
```

**Output**
```text
2025-07-20 10:15:23 ERROR Database connection failed
```

**DevOps Use Case:** Find errors or specific keywords in application logs.

> 💡 Common Options:
>
> - `-i` → Ignore case
> - `-r` → Search recursively
> - `-n` → Show line numbers
>
> Example:
> ```bash
> grep -i "error" app.log
> ```

---

# awk

**Purpose:** Extracts and processes columns from text files.

**Syntax**
```bash
awk '{print $column_number}' <file>
```

**Example**
```bash
df -h | awk '{print $5}'
```

**Output**
```text
Use%
45%
62%
```

**DevOps Use Case:** Extract CPU usage, memory usage, IP addresses, or specific log fields.

> 💡 Print the first column:
>
> ```bash
> awk '{print $1}' users.txt
> ```

---

# sed

**Purpose:** Searches and replaces text in files or command output.

**Syntax**
```bash
sed 's/old/new/' <file>
```

**Example**
```bash
sed 's/http/https/' config.txt
```

**Output**
```text
https://example.com
```

**DevOps Use Case:** Update configuration files or environment variables during deployments.

> 💡 Replace text directly in a file:
>
> ```bash
> sed -i 's/8080/9090/' application.properties
> ```

---

# Common Command Combinations

These one-liners are frequently used by DevOps Engineers.

---

## Find a Running Process

```bash
ps -ef | grep nginx
```

**Use Case:** Verify whether Nginx or any application is running.

---

## Monitor Logs in Real Time

```bash
tail -f app.log | grep ERROR
```

**Use Case:** Watch only error messages while troubleshooting.

---

## Find Disk Usage

```bash
df -h | grep "/"
```

**Use Case:** Check the usage of the root filesystem.

---

## Find Large Directories

```bash
du -sh * | sort -h
```

**Use Case:** Identify folders consuming the most disk space.

---

## List Open Ports

```bash
ss -tuln
```

**Use Case:** Verify whether your application is listening on the correct port.

---

## Check Service Status

```bash
systemctl status nginx
```

**Use Case:** Verify if a service is running after deployment.

---

## Restart a Service

```bash
sudo systemctl restart nginx
```

**Use Case:** Apply configuration changes or restart a failed service.

---

## Find Files

```bash
find /var/log -name "*.log"
```

**Use Case:** Locate log files quickly.

---

## Check Memory Usage

```bash
free -h
```

**Use Case:** Verify available RAM while troubleshooting application performance.

---

## Download and Test an API

```bash
curl http://localhost:8080/health
```

**Use Case:** Verify that an application or API is responding.

---

## 🎯 Quick Revision Tips

| Command | Purpose |
|----------|---------|
| `grep` | Search text or patterns |
| `awk` | Extract columns from text |
| `sed` | Find and replace text |
| `find` | Search files and directories |
| `systemctl` | Manage Linux services |
| `tail -f` | Monitor logs in real time |
| `curl` | Test APIs |
| `ss -tuln` | View listening ports |

---

## 💡 Common DevOps Workflow

When an application is not working after deployment:

```bash
systemctl status nginx
ps -ef | grep java
ss -tuln
tail -f /var/log/app.log
grep "ERROR" /var/log/app.log
free -h
df -h
curl http://localhost:8080/health
```

These commands help identify whether the issue is related to the service, process, network, logs, memory, disk space, or application health.

---

## ⭐ Interview Tips

- `grep`, `awk`, and `sed` are among the most commonly asked Linux commands in DevOps interviews.
- Learn how to combine commands using the **pipe (`|`)**.
- Practice reading logs, filtering output, and extracting useful information.
- Remember: **Linux commands become powerful when combined together.**

### Example

```bash
ps -ef | grep java | awk '{print $2}'
```

**What it does:** Finds the PID (Process ID) of a running Java application.

This is a common command used before stopping a process using:

```bash
kill <PID>
```

---

> 💡 **Final Tip:** You don't need to memorize every Linux command. Focus on understanding **what each command does**, **when to use it**, and **how to combine commands**. These practical skills are what interviewers and real-world DevOps tasks emphasize.