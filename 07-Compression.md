# 📦 Compression Commands

This section covers Linux commands used to compress, extract, and archive files. These commands are commonly used by DevOps Engineers to create backups, transfer files efficiently, and package applications.

---

# zip

**Purpose:** Compresses one or more files into a `.zip` archive.

**Syntax**
```bash
zip <archive_name>.zip <file_name>
```

**Example**
```bash
zip logs.zip app.log
```

**Output**
```text
adding: app.log (deflated 65%)
```

**DevOps Use Case:** Compress log files or reports before sharing or archiving.

---

# gunzip

**Purpose:** Extracts files compressed with `gzip` (`.gz`).

**Syntax**
```bash
gunzip <file>.gz
```

**Example**
```bash
gunzip backup.sql.gz
```

**Output**
```text
backup.sql
```

**DevOps Use Case:** Extract compressed database backups or log files received from another server.

> 💡 If you only want to view a `.gz` file without extracting it, use:
>
> ```bash
> zcat file.gz
> ```

---

# tar

**Purpose:** Archives multiple files or directories into a single file. It can also compress the archive.

**Syntax**
```bash
tar [options] <archive_name>.tar <directory>
```

### Create a Compressed Archive

```bash
tar -czf backup.tar.gz project/
```

**Output**
```text
backup.tar.gz created
```

### Extract an Archive

```bash
tar -xzf backup.tar.gz
```

**Output**
```text
Files extracted successfully.
```

**DevOps Use Case:** Create backups of application directories before deployment or migration.

> 💡 Common Options:
>
> - `-c` → Create archive
> - `-x` → Extract archive
> - `-z` → Compress using gzip
> - `-v` → Verbose (shows progress)
> - `-f` → Specify archive file

---

## 🎯 Quick Revision Tips

- **zip** → Compress files into a `.zip` archive.
- **gunzip** → Extract `.gz` files.
- **tar -czf** → Create a compressed archive.
- **tar -xzf** → Extract a compressed archive.

---

## 💡 Common DevOps Workflow

Backup an application before deployment:

```bash
tar -czf app-backup.tar.gz /var/www/html
```

Restore the backup later:

```bash
tar -xzf app-backup.tar.gz
```

This is a common practice before application upgrades or server migrations.

---

> 💡 **Interview Tip:** While `zip` is widely used across different operating systems, **`tar` is the preferred command in Linux environments** because it efficiently archives entire directories and preserves file permissions. You'll frequently use `tar` for backups, deployments, and log archiving in DevOps.