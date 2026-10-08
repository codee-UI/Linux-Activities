# Linux Filtering with `grep`, Pipes, and `find` — Concise Summary

## Objective
Learn how to filter information in Linux using:
- `grep` — search file contents for specific text
- `|` — pipe output from one command into another
- `find` — locate files and directories using search criteria

These commands help security analysts quickly locate logs, users, suspicious files, and relevant text.

## 1. `grep` — Search Inside Files

Syntax:

```bash
grep SEARCH_TEXT FILE
```

Examples:

```bash
grep OS updates.txt
grep error server_logs.txt
```

### Lab task

```bash
cd /home/analyst/logs
grep error server_logs.txt
```

**Result:** `server_logs.txt` contains **6 error entries**.

## 2. Piping with `|`

A pipe sends the output of one command to another command.

```bash
command1 | command2
```

Example:

```bash
ls | grep Q1
```

This lists files and then keeps only filenames containing `Q1`.

### Lab results

```bash
cd /home/analyst/reports/users
ls | grep Q1
```

**Result:** **3 files** contain `Q1`.

```bash
ls | grep access
```

**Result:** **4 files** contain `access`.

## 3. Search File Contents with `grep`

Find a specific username:

```bash
grep jhill Q2_deleted_users.txt
```

**Result:** `jhill` is present.

Find users in Human Resources:

```bash
grep "Human Resources" Q4_added_users.txt
```

Quotation marks are useful when the search phrase contains spaces.

## 4. `find` — Locate Files and Directories

Basic syntax:

```bash
find LOCATION CRITERIA
```

Example:

```bash
find /home/analyst/projects
```

### Find by filename

Case-sensitive:

```bash
find /home/analyst/projects -name "*log*"
```

Case-insensitive:

```bash
find /home/analyst/projects -iname "*log*"
```

The wildcard `*` represents zero or more unknown characters.

## 5. Search by Modification Time

Modified within the last 3 days:

```bash
find /home/analyst/projects -mtime -3
```

Modified more than 1 day ago:

```bash
find /home/analyst/projects -mtime +1
```

Modified less than 1 day ago:

```bash
find /home/analyst/projects -mtime -1
```

For minute-based searches, use:

```bash
-mmin
```

## Command Summary

| Command | Purpose | Example |
|---|---|---|
| `grep` | Search inside files | `grep error server_logs.txt` |
| `|` | Send output to another command | `ls | grep Q1` |
| `find` | Search files/directories | `find /home/analyst/projects -name "*log*"` |
| `-name` | Case-sensitive name search | `find . -name "*log*"` |
| `-iname` | Case-insensitive name search | `find . -iname "*log*"` |
| `-mtime` | Search by modification time in days | `find . -mtime -3` |
| `-mmin` | Search by modification time in minutes | `find . -mmin -30` |

## Complete Lab Workflow

```bash
cd /home/analyst/logs
grep error server_logs.txt

cd /home/analyst/reports/users
ls | grep Q1
ls | grep access

ls
grep jhill Q2_deleted_users.txt
grep "Human Resources" Q4_added_users.txt
```

## Lab Answers

| Question | Answer |
|---|---|
| Error lines in `server_logs.txt` | **6** |
| Files containing `Q1` | **3** |
| Files containing `access` | **4** |
| Is `jhill` in `Q2_deleted_users.txt`? | **Yes** |
| Find HR users | `grep "Human Resources" Q4_added_users.txt` |

## Security Relevance

These commands are useful for:
- Searching logs
- Finding error messages
- Locating users or events
- Finding suspicious filenames
- Searching recently modified files
- Reducing large outputs to relevant information

## Core Takeaway

Use:

```bash
grep
```

to search **inside files**,

```bash
|
```

to pass output between commands,

and:

```bash
find
```

to locate **files and directories** based on specific criteria.
