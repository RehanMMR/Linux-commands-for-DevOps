# 💾 Disk Usage Commands

This section covers Linux commands used to monitor disk space and analyze storage usage. These commands are commonly used by DevOps Engineers to troubleshoot storage issues and manage server resources.

---

# df

**Purpose:** Displays the available and used disk space of mounted filesystems.

**Syntax**
```bash
df
```

**Example**
```bash
df
```

**Output**
```text
Filesystem     1K-blocks     Used Available Use%
/dev/sda1       20511356 10485760 10025596  52%
```

**DevOps Use Case:** Check if a server is running out of disk space before deployments.

---

# df -h

**Purpose:** Displays disk usage in a human-readable format (KB, MB, GB).

**Syntax**
```bash
df -h
```

**Example**
```bash
df -h
```

**Output**
```text
Filesystem      Size  Used Avail Use%
/dev/sda1        20G   10G   9.6G  52%
```

**DevOps Use Case:** One of the most frequently used commands to quickly check available disk space on production servers.

> 💡 **Tip:** Always prefer `df -h` over `df` because the output is much easier to read.

---

# du

**Purpose:** Displays the disk space used by files and directories.

**Syntax**
```bash
du [options] <directory>
```

**Example**
```bash
du -sh /var/log
```

**Output**
```text
450M    /var/log
```

**DevOps Use Case:** Find which application, log folder, or backup directory is consuming disk space.

> 💡 Common Options:
>
> - `-h` → Human-readable sizes
> - `-s` → Show only the total size
>
> Example:
> ```bash
> du -sh *
> ```
> Displays the size of each file and folder in the current directory.

---

## 🎯 Quick Revision Tips

- **df** → Check filesystem disk usage.
- **df -h** → Check disk usage in a readable format (**Most Used**).
- **du** → Check the size of files and directories.
- **du -sh** → Show the total size of a directory (**Most Used**).

---

> 💡 **Interview Tip:** If a production server reports **"No space left on device"**, the first commands most DevOps Engineers run are:
>
> ```bash
> df -h
> du -sh /var/log
> ```
>
> These quickly help identify whether the disk is full and which directory is consuming the most space.