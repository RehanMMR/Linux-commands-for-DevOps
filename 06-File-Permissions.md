# 🔐 File Permissions

This section covers Linux commands used to manage file ownership and permissions. These commands are essential for controlling who can read, write, or execute files and directories.

---

# ls -l

**Purpose:** Displays detailed file information, including permissions, owner, and group.

**Syntax**
```bash
ls -l
```

**Example**
```bash
ls -l
```

**Output**
```text
-rwxr-xr-- 1 ubuntu developers 2048 Jul 20 deploy.sh
```

### Understanding the Output

```text
-rwxr-xr--
││ │ │
││ │ └── Others (r--)
││ └──── Group (r-x)
│└────── Owner (rwx)
└──────── File Type (- = File, d = Directory)
```

**DevOps Use Case:** Check whether deployment scripts or configuration files have the correct permissions.

---

# chmod

**Purpose:** Changes file or directory permissions.

**Syntax**
```bash
chmod <permissions> <file>
```

## Permission Numbers

| Number | Permission | Meaning |
|---------|------------|---------|
| 7 | rwx | Read + Write + Execute |
| 6 | rw- | Read + Write |
| 5 | r-x | Read + Execute |
| 4 | r-- | Read Only |
| 3 | -wx | Write + Execute |
| 2 | -w- | Write Only |
| 1 | --x | Execute Only |
| 0 | --- | No Permission |

### Easy Way to Remember

```text
Read    = 4
Write   = 2
Execute = 1

Add them together:

7 = 4+2+1 = rwx
6 = 4+2   = rw-
5 = 4+1   = r-x
4 = 4     = r--
```

---

### Common Permission Examples

| Permission | Meaning |
|------------|---------|
| 777 | Everyone has full access (Not Recommended) |
| 755 | Owner: Full, Group/Others: Read & Execute |
| 744 | Owner: Full, Others: Read Only |
| 700 | Only owner has access |
| 600 | Owner can Read & Write (Best for private files) |

---

**Example**
```bash
chmod 755 deploy.sh
```

**Output**
```text
Permissions updated.
```

**DevOps Use Case:** Make deployment or shell scripts executable before running them.

> 💡 **Common Example**
>
> ```bash
> chmod +x deploy.sh
> ```
>
> Adds execute permission to a script.

---

# umask

**Purpose:** Sets the default permissions for newly created files and directories.

**Syntax**
```bash
umask
```

**Example**
```bash
umask 022
```

**Output**
```text
New files: 644
New directories: 755
```

**DevOps Use Case:** Configure default permissions so newly created files are secure.

---

# chown

**Purpose:** Changes the owner of a file or directory.

**Syntax**
```bash
sudo chown <owner> <file>
```

**Example**
```bash
sudo chown ubuntu app.log
```

**Output**
```text
Owner changed successfully.
```

**DevOps Use Case:** Change ownership of application files after deployment.

> 💡 Change owner recursively:
>
> ```bash
> sudo chown -R ubuntu:ubuntu /var/www/html
> ```

---

# chgrp

**Purpose:** Changes the group ownership of a file or directory.

**Syntax**
```bash
sudo chgrp <group> <file>
```

**Example**
```bash
sudo chgrp developers deploy.sh
```

**Output**
```text
Group changed successfully.
```

**DevOps Use Case:** Give a development team access to shared project files.

---

## 🎯 Quick Revision Tips

- **ls -l** → View file permissions.
- **chmod** → Change file permissions.
- **chmod +x** → Make a file executable.
- **chmod 755** → Most common permission for scripts.
- **chmod 600** → Best for private keys.
- **umask** → Set default permissions.
- **chown** → Change file owner.
- **chgrp** → Change group ownership.

---

## 💡 Common DevOps Workflow

```bash
ls -l deploy.sh
chmod +x deploy.sh
sudo chown ubuntu:developers deploy.sh
```

This workflow ensures the deployment script has the correct permissions and ownership before execution.

---

## ⚠️ Interview Tips

### Why is `chmod 777` not recommended?

It gives **Read, Write, and Execute** permissions to **everyone**, creating a serious security risk.

---

### Why should SSH private keys have `600` permission?

```bash
chmod 600 ~/.ssh/id_rsa
```

This ensures **only the owner** can read and write the private key. SSH may refuse to use the key if its permissions are too open.

---

### Most Common Permissions

| Permission | Used For |
|------------|----------|
| **755** | Shell scripts & application directories |
| **644** | Configuration and text files |
| **600** | SSH private keys & sensitive files |
| **700** | Private directories |

> 💡 **Interview Tip:** `chmod`, `chown`, and `ls -l` are among the most frequently used Linux commands in DevOps. Understanding permission numbers like **755**, **644**, and **600** is a common interview topic and essential for managing secure Linux systems.