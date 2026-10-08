# Linux Permissions and Authorization — Concise Summary

## Objective

Learn how Linux file and directory permissions work and how to modify them using `chmod` while applying the **principle of least privilege**.

Main commands:

- `ls -l` — view file/directory permissions
- `ls -a` — show hidden files
- `ls -la` — show permissions including hidden files
- `chmod` — change permissions

---

# Permission Structure

Linux permissions are shown as a **10-character string**.

Example:

```text
drwxrwxrwx
```

## Character Meaning

| Position | Meaning |
|---|---|
| 1 | File type: `d` = directory, `-` = regular file |
| 2–4 | User permissions |
| 5–7 | Group permissions |
| 8–10 | Other-user permissions |

Permission letters:

- `r` = read
- `w` = write
- `x` = execute
- `-` = permission not granted

Example:

```text
-rw-r-----
```

means:

- User: read + write
- Group: read only
- Other: no permissions

---

# Permission Meaning

## Files

- `r` — read file contents
- `w` — modify file contents
- `x` — execute the file

## Directories

- `r` — list directory contents
- `w` — create or remove items in the directory
- `x` — enter/access the directory

---

# Viewing Permissions

Show detailed permissions:

```bash
ls -l
```

Show hidden files:

```bash
ls -a
```

Show detailed permissions including hidden files:

```bash
ls -la
```

---

# Changing Permissions with `chmod`

## Owner Types

| Symbol | Meaning |
|---|---|
| `u` | User/owner |
| `g` | Group |
| `o` | Other users |

## Operators

| Symbol | Meaning |
|---|---|
| `+` | Add permission |
| `-` | Remove permission |
| `=` | Set permissions exactly |

## Examples

Add all permissions:

```bash
chmod u+rwx,g+rwx,o+rwx login_sessions.txt
```

Remove all permissions:

```bash
chmod u-rwx,g-rwx,o-rwx login_sessions.txt
```

Set everyone to read-only:

```bash
chmod u=r,g=r,o=r login_sessions.txt
```

Remove group read/write access:

```bash
chmod g-rw bonuses.txt
```

---

# Principle of Least Privilege

The **principle of least privilege** means users should receive only the minimum permissions required to perform their work.

Example:

If a confidential file has:

```text
-rw-rw----
```

and only the owner should access it, remove group permissions:

```bash
chmod g-rw bonuses.txt
```

This reduces unnecessary access.

---

# Lab Scenario

User:

```text
researcher2
```

Group:

```text
research_team
```

Working directory:

```text
/home/researcher2/projects
```

Goal: inspect and correct permissions on files, hidden files, and the `drafts` directory.

---

# Task 1 — Inspect Permissions

Navigate to the projects directory:

```bash
cd projects
```

View permissions:

```bash
ls -l
```

Example entries:

```text
drwx--x--- drafts
-rw-rw-rw- project_k.txt
-rw-r----- project_m.txt
-rw-rw-r-- project_r.txt
-rw-rw-r-- project_t.txt
```

### Answers

- Group owner: **`research_team`**
- Hidden file: **`.project_x.txt`**

Check hidden files with:

```bash
ls -la
```

---

# Task 2 — Correct File Permissions

## Remove write permission for `other`

Problem file:

```text
project_k.txt
```

Command:

```bash
chmod o-w project_k.txt
```

## Restrict `project_m.txt`

The group currently has:

```text
read only
```

Remove group read access:

```bash
chmod g-r project_m.txt
```

This leaves the restricted file accessible only to the user as required.

---

# Task 3 — Fix Hidden File Permissions

Hidden file:

```text
.project_x.txt
```

The user and group both have incorrect write permissions.

Required state:

- User: read, no write
- Group: read, no write

Command:

```bash
chmod u-w,g-w,g+r .project_x.txt
```

---

# Task 4 — Restrict the `drafts` Directory

The group currently has execute permission and can access the directory.

Remove group execute permission:

```bash
chmod g-x drafts
```

Now only `researcher2` should be able to access the directory.

---

# Complete Lab Workflow

```bash
cd /home/researcher2/projects

ls -l
ls -la

chmod o-w project_k.txt

chmod g-r project_m.txt

chmod u-w,g-w,g+r .project_x.txt

chmod g-x drafts

ls -la
```

---

# Lab Answers

| Question | Answer |
|---|---|
| Group owning project files | `research_team` |
| Hidden file | `.project_x.txt` |
| File allowing other users to write | `project_k.txt` |
| Group permissions on `project_m.txt` | Read only |
| Incorrect write permissions on `.project_x.txt` | User and group |
| Does group have access to `drafts` initially? | Yes |

---

# Command Summary

| Command | Purpose |
|---|---|
| `ls -l` | Show detailed permissions |
| `ls -a` | Show hidden files |
| `ls -la` | Show permissions including hidden files |
| `chmod` | Change permissions |
| `chmod o-w file` | Remove write from others |
| `chmod g-r file` | Remove group read |
| `chmod g-x dir` | Remove group directory access |

---

# Security Relevance

Permission management helps security analysts:

- Prevent unauthorized access
- Protect confidential files
- Enforce least privilege
- Limit access to sensitive directories
- Reduce accidental or malicious modification
- Audit user, group, and other permissions
- Secure hidden and archived files

---

# Core Takeaway

The essential permission-management commands are:

```bash
ls -l
ls -la
chmod
```

Always inspect permissions first, identify unnecessary access, and then use `chmod` to enforce the **principle of least privilege**.
