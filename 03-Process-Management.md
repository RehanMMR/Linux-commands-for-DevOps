# ⚙️ Process Management Commands

This section covers Linux commands used to monitor, manage, and troubleshoot running processes. These are essential for DevOps Engineers to identify resource usage, stop unresponsive applications, and monitor server health.

---

# top

**Purpose:** Displays real-time information about running processes, CPU usage, and memory usage.

**Syntax**
```bash
top
```

**Example**
```bash
top
```

**Output**
```text
PID   USER   %CPU  %MEM  COMMAND
1234  root   45.2   8.1  java
5678  nginx   2.1   1.0  nginx
```

**DevOps Use Case:** Monitor server performance and identify processes consuming high CPU or memory.

> 💡 Press **q** to exit `top`.

---

# ps

**Purpose:** Displays information about running processes.

**Syntax**
```bash
ps [options]
```

**Example**
```bash
ps -ef
```

**Output**
```text
UID   PID  PPID  CMD
root 1234     1  java -jar app.jar
root 5678     1  nginx
```

**DevOps Use Case:** Verify if an application or service is running after deployment.

> 💡 Commonly used with `grep`:
>
> ```bash
> ps -ef | grep nginx
> ```

---

# fuser

**Purpose:** Shows which process is using a file, directory, or port.

**Syntax**
```bash
fuser <file_or_port>
```

**Example**
```bash
fuser 8080/tcp
```

**Output**
```text
8080/tcp: 2456
```

**DevOps Use Case:** Identify which application is occupying a port before starting a new service.

---

# kill

**Purpose:** Terminates a running process using its Process ID (PID).

**Syntax**
```bash
kill <PID>
```

**Example**
```bash
kill 2456
```

**Output**
```text
(Process terminated)
```

**DevOps Use Case:** Stop a stuck or unresponsive application.

> 💡 Force kill a process:
>
> ```bash
> kill -9 2456
> ```

---

# free

**Purpose:** Displays system memory usage.

**Syntax**
```bash
free
```

**Example**
```bash
free -h
```

**Output**
```text
              total   used   free
Mem:            8Gi    3Gi    5Gi
Swap:           2Gi    0Gi    2Gi
```

**DevOps Use Case:** Check available RAM before deploying memory-intensive applications.

> 💡 Use `free -h` for human-readable output.

---

# nohup

**Purpose:** Runs a command in the background even after logging out.

**Syntax**
```bash
nohup <command> &
```

**Example**
```bash
nohup java -jar app.jar &
```

**Output**
```text
Output written to nohup.out
```

**DevOps Use Case:** Keep applications running after disconnecting from an SSH session.

---

# vmstat

**Purpose:** Displays CPU, memory, process, and I/O statistics.

**Syntax**
```bash
vmstat
```

**Example**
```bash
vmstat 2
```

**Output**
```text
procs --------memory-------- ---cpu---
r  b   swpd   free   buff  cache
1  0      0 524288  10240 256000
```

**DevOps Use Case:** Diagnose CPU, memory, or performance bottlenecks on Linux servers.

---

# vmstat -a

**Purpose:** Displays active and inactive memory along with system statistics.

**Syntax**
```bash
vmstat -a
```

**Example**
```bash
vmstat -a
```

**Output**
```text
procs --------memory--------
active inactive free
204800  102400  524288
```

**DevOps Use Case:** Analyze memory utilization while troubleshooting application performance.

---

## 🎯 Quick Revision Tips

- **top** → Monitor CPU and memory usage in real time.
- **ps -ef** → List all running processes.
- **fuser** → Find which process is using a file or port.
- **kill** → Stop a running process.
- **kill -9** → Force stop a process.
- **free -h** → Check available memory.
- **nohup** → Run a process in the background after logout.
- **vmstat** → View CPU, memory, and system performance statistics.

---

> 💡 **Interview Tip:** When an application becomes slow or unresponsive, a DevOps Engineer typically checks:
>
> ```bash
> top
> ps -ef | grep <application_name>
> free -h
> vmstat 2
> ```
>
> These commands quickly help identify whether the issue is related to CPU, memory, or a stuck process.