# 👤 User & Group Management Commands

This section covers Linux commands used to create, manage, and remove users and groups. These commands are commonly used by DevOps Engineers to manage server access and permissions.

---

# useradd -m

**Purpose:** Creates a new user with a home directory.

**Syntax**
```bash
sudo useradd -m <username>
```

**Example**
```bash
sudo useradd -m devuser
```

**Output**
```text
(User created successfully)
```

**DevOps Use Case:** Create a new user account for a developer or administrator on a Linux server.

---

# passwd

**Purpose:** Sets or changes a user's password.

**Syntax**
```bash
sudo passwd <username>
```

**Example**
```bash
sudo passwd devuser
```

**Output**
```text
New password:
Retype new password:
passwd: password updated successfully
```

**DevOps Use Case:** Set the password after creating a new user account.

---

# su

**Purpose:** Switches to another user account.

**Syntax**
```bash
su <username>
```

**Example**
```bash
su devuser
```

**Output**
```text
Password:
```

**DevOps Use Case:** Test whether a newly created user can log in successfully.

> 💡 To switch to the root user:
> ```bash
> sudo su
> ```

---

# userdel

**Purpose:** Deletes an existing user.

**Syntax**
```bash
sudo userdel <username>
```

**Example**
```bash
sudo userdel devuser
```

**Output**
```text
(User deleted)
```

**DevOps Use Case:** Remove accounts of employees who no longer require server access.

> 💡 Delete the user's home directory as well:
> ```bash
> sudo userdel -r devuser
> ```

---

# groupadd

**Purpose:** Creates a new group.

**Syntax**
```bash
sudo groupadd <group_name>
```

**Example**
```bash
sudo groupadd developers
```

**Output**
```text
(Group created successfully)
```

**DevOps Use Case:** Create groups to manage permissions for teams like Developers, QA, or DevOps.

---

# cat /etc/group

**Purpose:** Displays all groups available on the system.

**Syntax**
```bash
cat /etc/group
```

**Example**
```bash
cat /etc/group
```

**Output**
```text
root:x:0:
sudo:x:27:
developers:x:1002:
```

**DevOps Use Case:** Verify whether a group exists before adding users to it.

---

# gpasswd -a

**Purpose:** Adds a user to an existing group.

**Syntax**
```bash
sudo gpasswd -a <username> <group_name>
```

**Example**
```bash
sudo gpasswd -a devuser developers
```

**Output**
```text
Adding user devuser to group developers
```

**DevOps Use Case:** Grant users access to shared project files or Docker by adding them to the appropriate group.

---

# gpasswd -M

**Purpose:** Assigns multiple users to a group.

**Syntax**
```bash
sudo gpasswd -M <user1,user2,user3> <group_name>
```

**Example**
```bash
sudo gpasswd -M alice,bob,charlie developers
```

**Output**
```text
(Group members updated)
```

**DevOps Use Case:** Quickly assign an entire team to a shared group.

> 💡 This command replaces the existing group members with the specified list.

---

# groupdel

**Purpose:** Deletes an existing group.

**Syntax**
```bash
sudo groupdel <group_name>
```

**Example**
```bash
sudo groupdel developers
```

**Output**
```text
(Group deleted)
```

**DevOps Use Case:** Remove unused groups to keep the system organized.

---

## 🎯 Quick Revision Tips

- **useradd -m** → Create a new user with a home directory.
- **passwd** → Set or change a user's password.
- **su** → Switch to another user.
- **userdel -r** → Delete a user and their home directory.
- **groupadd** → Create a new group.
- **cat /etc/group** → View all groups.
- **gpasswd -a** → Add a user to a group.
- **gpasswd -M** → Add multiple users to a group.
- **groupdel** → Delete a group.

---

## 💡 Common DevOps Workflow

Create a new user and add them to a team:

```bash
sudo useradd -m devuser
sudo passwd devuser
sudo groupadd developers
sudo gpasswd -a devuser developers
```

This workflow is commonly used when onboarding a new team member who needs access to Linux servers.

---

> 💡 **Interview Tip:** User and group management is a fundamental Linux administration skill. As a DevOps Engineer, you'll frequently create users, assign group permissions, and manage access to production servers.