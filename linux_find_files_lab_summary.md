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
