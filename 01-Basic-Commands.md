# 📁 Basic Linux Commands

This section covers the most commonly used Linux commands for file and directory management. These commands are essential for anyone working with Linux, especially DevOps Engineers who frequently access remote servers.

---

# ls

**Purpose:** Lists files and directories in the current location.

**Syntax**
```bash
ls [options]
```

**Example**
```bash
ls -l
```

**Output**
```text
drwxr-xr-x  Projects
-rw-r--r--  app.log
```

**DevOps Use Case:** Verify application files after deploying to a server.

---

# mkdir

**Purpose:** Creates a new directory.

**Syntax**
```bash
mkdir <directory_name>
```

**Example**
```bash
mkdir project
```

**Output**
```text
project/
```

**DevOps Use Case:** Create directories for application logs, backups, or deployment scripts.

---

# pwd

**Purpose:** Displays the current working directory.

**Syntax**
```bash
pwd
```

**Example**
```bash
pwd
```

**Output**
```text
/home/ubuntu/projects
```

**DevOps Use Case:** Confirm you're in the correct directory before executing deployment commands.

---

# touch

**Purpose:** Creates an empty file or updates the timestamp of an existing file.

**Syntax**
```bash
touch <file_name>
```

**Example**
```bash
touch app.log
```

**Output**
```text
app.log
```

**DevOps Use Case:** Create log, configuration, or placeholder files.

---

# cd

**Purpose:** Changes the current directory.

**Syntax**
```bash
cd <directory>
```

**Example**
```bash
cd /var/log
```

**Output**
```text
(Current directory changes to /var/log)
```

**DevOps Use Case:** Navigate to application, configuration, or log directories.

---

# rm

**Purpose:** Deletes a file.

**Syntax**
```bash
rm <file_name>
```

**Example**
```bash
rm app.log
```

**Output**
```text
(File removed)
```

**DevOps Use Case:** Remove temporary or old log files.

> ⚠️ Deleted files cannot be recovered easily.

---

# rm -r

**Purpose:** Deletes a directory and all its contents.

**Syntax**
```bash
rm -r <directory>
```

**Example**
```bash
rm -r old-backup
```

**Output**
```text
(Directory removed)
```

**DevOps Use Case:** Remove old deployment or backup directories.

---

# rmdir

**Purpose:** Deletes an empty directory.

**Syntax**
```bash
rmdir <directory>
```

**Example**
```bash
rmdir test-folder
```

**Output**
```text
(Directory removed)
```

**DevOps Use Case:** Clean up unused empty directories.

---

# cat

**Purpose:** Displays the contents of a file.

**Syntax**
```bash
cat <file_name>
```

**Example**
```bash
cat config.yml
```

**Output**
```text
server:
  port: 8080
```

**DevOps Use Case:** Quickly view configuration or log files.

---

# echo

**Purpose:** Displays text or writes text into a file.

**Syntax**
```bash
echo "text"
```

**Example**
```bash
echo "Deployment Successful"
```

**Output**
```text
Deployment Successful
```

**DevOps Use Case:** Write environment variables or generate simple configuration files.

---

# head

**Purpose:** Displays the first 10 lines of a file.

**Syntax**
```bash
head <file>
```

**Example**
```bash
head app.log
```

**Output**
```text
First 10 lines of app.log
```

**DevOps Use Case:** Quickly inspect the beginning of large log files.

---

# tail

**Purpose:** Displays the last 10 lines of a file.

**Syntax**
```bash
tail <file>
```

**Example**
```bash
tail app.log
```

**Output**
```text
Last 10 lines of app.log
```

**DevOps Use Case:** Check recent log entries after deploying an application.

---

# tail -f

**Purpose:** Monitors a file in real time.

**Syntax**
```bash
tail -f <file>
```

**Example**
```bash
tail -f app.log
```

**Output**
```text
New log entries appear automatically.
```

**DevOps Use Case:** Monitor application logs while debugging live services.

---

# less

**Purpose:** Views large files one page at a time.

**Syntax**
```bash
less <file>
```

**Example**
```bash
less app.log
```

**Output**
```text
Scrollable file view
```

**DevOps Use Case:** Read large log files without loading everything into memory.

---

# more

**Purpose:** Displays file contents page by page.

**Syntax**
```bash
more <file>
```

**Example**
```bash
more app.log
```

**Output**
```text
Page-by-page file view
```

**DevOps Use Case:** View lengthy configuration or log files.

---

# cp

**Purpose:** Copies files.

**Syntax**
```bash
cp <source> <destination>
```

**Example**
```bash
cp app.conf backup.conf
```

**Output**
```text
backup.conf created
```

**DevOps Use Case:** Backup configuration files before making changes.

---

# cp -r

**Purpose:** Copies directories recursively.

**Syntax**
```bash
cp -r <source> <destination>
```

**Example**
```bash
cp -r project backup-project
```

**Output**
```text
Entire directory copied
```

**DevOps Use Case:** Create deployment or project backups.

---

# mv

**Purpose:** Moves or renames files and directories.

**Syntax**
```bash
mv <source> <destination>
```

**Example**
```bash
mv app.log old-app.log
```

**Output**
```text
File renamed
```

**DevOps Use Case:** Archive old log files or rename deployment folders.

---

# wc

**Purpose:** Counts lines, words, and characters.

**Syntax**
```bash
wc <file>
```

**Example**
```bash
wc app.log
```

**Output**
```text
120 350 2450 app.log
```

**DevOps Use Case:** Count log entries or verify file size.

---

# Soft Link (Symbolic Link)

**Purpose:** Creates a shortcut to another file or directory.

**Syntax**
```bash
ln -s <target> <link_name>
```

**Example**
```bash
ln -s /var/log/app.log latest.log
```

**Output**
```text
latest.log -> /var/log/app.log
```

**DevOps Use Case:** Point applications to the latest release directory without changing configurations.

---

# Hard Link

**Purpose:** Creates another reference to the same file.

**Syntax**
```bash
ln <target> <link_name>
```

**Example**
```bash
ln app.log app_backup.log
```

**Output**
```text
Both files reference the same data.
```

**DevOps Use Case:** Keep multiple references to important files on the same filesystem.

> 💡 Hard links cannot be created for directories or across different filesystems.

---

# cut

**Purpose:** Extracts specific columns or fields from text.

**Syntax**
```bash
cut -d "<delimiter>" -f<field_number> <file>
```

**Example**
```bash
cut -d ":" -f1 /etc/passwd
```

**Output**
```text
root
ubuntu
mysql
```

**DevOps Use Case:** Extract usernames, IPs, or values from configuration files.

---

# tee

**Purpose:** Displays output and saves it to a file simultaneously.

**Syntax**
```bash
command | tee <file>
```

**Example**
```bash
ls -l | tee files.txt
```

**Output**
```text
(Output shown on screen and saved to files.txt)
```

**DevOps Use Case:** Save deployment logs while viewing them in real time.

---

# sort

**Purpose:** Sorts lines alphabetically or numerically.

**Syntax**
```bash
sort <file>
```

**Example**
```bash
sort users.txt
```

**Output**
```text
alice
bob
charlie
```

**DevOps Use Case:** Sort usernames, IP addresses, or log entries.

---

# diff

**Purpose:** Compares two files and shows differences.

**Syntax**
```bash
diff <file1> <file2>
```

**Example**
```bash
diff config-old.yml config-new.yml
```

**Output**
```text
Shows changed lines
```

**DevOps Use Case:** Compare configuration files before deployment.

---

# vi Editor

**Purpose:** Opens the Vim editor to create or edit files.

**Syntax**
```bash
vi <file_name>
```

**Example**
```bash
vi nginx.conf
```

**Output**
```text
Opens the file in Vim editor.
```

**DevOps Use Case:** Edit server configuration files directly on Linux servers.

### Useful Vim Shortcuts

| Command | Description |
|----------|-------------|
| `i` | Insert mode |
| `Esc` | Exit insert mode |
| `:w` | Save file |
| `:q` | Quit |
| `:wq` | Save and quit |
| `:q!` | Quit without saving |

---

## 🎯 Quick Revision Tips

- `ls` → List files
- `pwd` → Show current directory
- `cd` → Change directory
- `mkdir` → Create directory
- `touch` → Create file
- `cat` → View file
- `cp` → Copy
- `mv` → Move/Rename
- `rm` → Delete
- `tail -f` → Live log monitoring
- `tee` → Display and save output
- `diff` → Compare files
- `vi` → Edit files

> 💡 **Interview Tip:** These are the commands you'll use almost every day while working on Linux servers, troubleshooting applications, deploying software, and managing configurations in a DevOps environment.