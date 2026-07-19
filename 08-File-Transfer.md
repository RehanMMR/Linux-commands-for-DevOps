# 📤 File Transfer Commands

This section covers Linux commands used to securely transfer files between local and remote systems. These commands are widely used by DevOps Engineers for deployments, backups, and server migrations.

---

# ssh

**Purpose:** Securely connects to a remote Linux server.

**Syntax**
```bash
ssh <username>@<server_ip>
```

**Example**
```bash
ssh ubuntu@192.168.1.10
```

**Output**
```text
ubuntu@server:~$
```

**DevOps Use Case:** Connect to production or cloud servers (AWS EC2, Azure VM, GCP VM) for deployments and troubleshooting.

> 💡 Using an SSH key:
>
> ```bash
> ssh -i my-key.pem ubuntu@192.168.1.10
> ```

---

# scp

**Purpose:** Securely copies files between local and remote systems over SSH.

**Syntax**
```bash
scp [options] <source> <destination>
```

**Example**
```bash
scp -i my-key.pem app.jar ubuntu@192.168.1.10:/home/ubuntu/
```

**Output**
```text
app.jar                              100%  25MB   5.2MB/s
```

**DevOps Use Case:** Upload application files, scripts, or configuration files to a remote server.

> 💡 Copy a directory:
>
> ```bash
> scp -r project/ ubuntu@192.168.1.10:/home/ubuntu/
> ```

---

# rsync

**Purpose:** Synchronizes files and directories efficiently between systems.

**Syntax**
```bash
rsync [options] <source> <destination>
```

**Example**
```bash
rsync -av project/ ubuntu@192.168.1.10:/var/www/html/
```

**Output**
```text
sending incremental file list...
app.jar
config.yml

sent 5.2M bytes
```

**DevOps Use Case:** Deploy application updates or synchronize backups between servers without copying unchanged files.

> 💡 Common Options:
>
> - `-a` → Archive mode (preserves permissions)
> - `-v` → Verbose output
> - `-z` → Compress data during transfer
>
> Example:
>
> ```bash
> rsync -avz project/ ubuntu@192.168.1.10:/var/www/html/
> ```

---

## 🎯 Quick Revision Tips

- **ssh** → Connect to a remote server.
- **ssh -i** → Connect using an SSH private key.
- **scp** → Copy files securely between systems.
- **scp -r** → Copy an entire directory.
- **rsync** → Synchronize files efficiently.
- **rsync -avz** → Most commonly used options for deployments.

---

## 💡 Common DevOps Workflow

Connect to a server:

```bash
ssh -i my-key.pem ubuntu@192.168.1.10
```

Upload the application:

```bash
scp -i my-key.pem app.jar ubuntu@192.168.1.10:/home/ubuntu/
```

Deploy or sync application files:

```bash
rsync -avz project/ ubuntu@192.168.1.10:/var/www/html/
```

This is a common workflow for deploying applications to Linux servers.

---

> 💡 **Interview Tip:** While `scp` is simple and useful for copying files, **`rsync` is the preferred choice in DevOps** because it transfers only the changed files, making deployments much faster and reducing network usage.