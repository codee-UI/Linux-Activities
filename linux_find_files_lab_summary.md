# Linux File Navigation and Reading Files — Concise Summary

## Objective

Learn how to navigate the Linux filesystem and read file contents using common Bash commands.

Key topics:

- Filesystem Hierarchy Standard (FHS)
- Absolute and relative paths
- Navigation commands: `pwd`, `ls`, `cd`
- File-reading commands: `cat`, `head`, `tail`, `less`

---

## Filesystem Hierarchy Standard (FHS)

The **FHS** defines how Linux directories and files are organized.

The highest-level directory is:

```text
/
```

This is called the **root directory**.

Common directories include:

| Directory | Purpose |
|---|---|
| `/home` | User home directories |
| `/bin` | Binary files and executables |
| `/etc` | System configuration files |
| `/tmp` | Temporary files |
| `/mnt` | Mounted storage such as USB drives |

### User Home Directory

Example:

```text
/home/analyst
```

It can also be represented with:

```text
~
```

Example:

```text
/home/analyst/logs
```

is equivalent to:

```text
~/logs
```

---

## File Paths

### Absolute Path

Starts from the root directory:

```text
/home/analyst/projects
```

### Relative Path

Starts from the current directory:

```text
projects
```

Useful symbols:

| Symbol | Meaning |
|---|---|
| `.` | Current directory |
| `..` | Parent directory |
| `~` | User home directory |

Example:

```bash
cd ..
```

Moves up one directory level.

---

# Navigation Commands

## `pwd`

Shows the current working directory.

```bash
pwd
```

Example output:

```text
/home/analyst
```

---

## `whoami`

Shows the current username.

```bash
whoami
```

Example:

```text
analyst
```

---

## `ls`

Lists files and directories in the current directory.

```bash
ls
```

List another directory:

```bash
ls /home/analyst/projects
```

or:

```bash
ls projects
```

---

## `cd`

Changes the current directory.

Move into a subdirectory:

```bash
cd projects
```

Use an absolute path:

```bash
cd /home/analyst/logs
```

Move up one level:

```bash
cd ..
```

---

# Reading File Content

## `cat`

Displays the entire contents of a file.

```bash
cat updates.txt
```

Best for short files.

---

## `head`

Displays the beginning of a file.

By default:

```bash
head updates.txt
```

shows the first **10 lines**.

Show only the first 5 lines:

```bash
head -n 5 updates.txt
```

---

## `tail`

Displays the end of a file.

```bash
tail updates.txt
```

By default, it shows the last **10 lines**.

Useful for reviewing the most recent entries in log files.

---

## `less`

Displays file contents one page at a time.

```bash
less updates.txt
```

Useful keyboard controls:

| Key | Action |
|---|---|
| `Space` | Move forward one page |
| `b` | Move back one page |
| `↓` | Move forward one line |
| `↑` | Move back one line |
| `q` | Quit |

---

# Command Summary

| Command | Purpose |
|---|---|
| `pwd` | Show current directory |
| `whoami` | Show current username |
| `ls` | List files and directories |
| `cd` | Change directory |
| `cat` | Display full file contents |
| `head` | Display beginning of a file |
| `tail` | Display end of a file |
| `less` | View a file page by page |
| `man hier` | Learn more about the FHS |

---

# Example Workflow

```bash
pwd
ls
cd projects
ls
cat report.txt
head -n 5 report.txt
tail report.txt
less report.txt
cd ..
```

This workflow lets you:

1. Check your location
2. List directory contents
3. Enter a directory
4. Inspect files
5. Read full or partial file contents
6. Return to the parent directory

---

## Security Relevance

These commands are important for security analysts because they help with:

- Navigating system directories
- Inspecting configuration files
- Reviewing logs
- Examining reports
- Investigating suspicious files
- Understanding file locations

---

## Core Takeaway

The essential navigation commands are:

```bash
pwd
ls
cd
```

The essential file-reading commands are:

```bash
cat
head
tail
less
```

Mastering these commands is a foundation for Linux administration and cybersecurity analysis.


# Linux File Navigation Lab — Concise Task Summary

## Objective
Practice finding and reading files in Linux using basic Bash commands.

Main commands:
- `pwd` — show current directory
- `ls` — list files and directories
- `cd` — change directories
- `cat` — display full file contents
- `head` — display the first lines of a file

## Task 1 — Check the Current Directory

```bash
pwd
ls
```

Expected current directory:

```text
/home/analyst
```

Use `ls` to count how many directories are present.

## Task 2 — Navigate to the Reports Directory

```bash
cd /home/analyst/reports
ls
```

Subdirectory to identify:

```text
users
```

## Task 3 — Read a User Report

```bash
cd /home/analyst/reports/users
ls
cat Q1_added_users.txt
```

Use the file contents to answer:
- What department does user `aezra` work in?
- What is the `employee_id` of user `mreed` in the Information Technology department?

## Task 4 — Inspect a Log File

```bash
cd /home/analyst/logs
ls
head -n 10 server_logs.txt
```

Count how many warning messages appear in the first 10 lines.

## Command Summary

| Command | Purpose | Example |
|---|---|---|
| `pwd` | Show current directory | `pwd` |
| `ls` | List files/directories | `ls` |
| `cd` | Change directory | `cd /home/analyst/reports` |
| `cat` | Show full file contents | `cat Q1_added_users.txt` |
| `head` | Show first lines | `head -n 10 server_logs.txt` |

## Complete Workflow

```bash
pwd
ls

cd /home/analyst/reports
ls

cd /home/analyst/reports/users
ls
cat Q1_added_users.txt

cd /home/analyst/logs
ls
head -n 10 server_logs.txt
```

## Skills Practiced
- Identify the current working directory
- List directory contents
- Navigate with absolute paths
- Locate files
- Read full file contents
- Inspect the beginning of log files
- Extract information from reports and logs

## Security Relevance
These commands are useful for:
- Reviewing user-access reports
- Investigating unauthorized access
- Inspecting system logs
- Locating evidence
- Working remotely without a graphical interface

## Core Takeaway

```bash
pwd
ls
cd
cat
head
```

These five commands provide a basic workflow for navigating Linux and examining files during security investigations.
