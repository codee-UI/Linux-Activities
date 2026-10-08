# Linux Filtering with `grep`, Pipes, and `find` — Concise Summary

## Objective
Learn how to filter information in Linux using:

- `grep` — search file contents for matching text
- `|` — pipe output from one command into another
- `find` — locate files and directories using search criteria

## `grep` — Search Inside Files

Syntax:

```bash
grep SEARCH_TERM FILE
```

Examples:

```bash
grep OS updates.txt
grep error time_logs.txt
```

Useful for finding errors, usernames, IP addresses, or suspicious events in logs.

## Piping with `|`

A pipe sends the output of one command into another.

Example:

```bash
ls /home/analyst/reports | grep users
```

General pattern:

```bash
COMMAND1 | COMMAND2
```

## `find` — Search for Files and Directories

Basic syntax:

```bash
find STARTING_DIRECTORY CRITERIA
```

Example:

```bash
find /home/analyst/projects
```

### `-name`

Case-sensitive filename search:

```bash
find /home/analyst/projects -name "*log*"
```

### `-iname`

Case-insensitive filename search:

```bash
find /home/analyst/projects -iname "*log*"
```

### Wildcard `*`

Represents zero or more unknown characters.

Example:

```text
*log*
```

### `-mtime`

Search by modification time in days:

```bash
find /home/analyst/projects -mtime -3
find /home/analyst/projects -mtime +1
find /home/analyst/projects -mtime -1
```

### `-mmin`

Search by modification time in minutes:

```bash
find /home/analyst/projects -mmin -30
```

# Lab: Filter with `grep`

## Task 1 — Find Error Messages

```bash
cd /home/analyst/logs
grep error server_logs.txt
```

Goal: count how many lines contain `error`.

## Task 2 — Find Filenames Containing Text

```bash
cd /home/analyst/reports/users
ls | grep Q1
```

Goal: count filenames containing `Q1`.

Then:

```bash
ls | grep access
```

Goal: count filenames containing `access`.

## Command Summary

| Command | Purpose | Example |
|---|---|---|
| `grep` | Search text inside a file | `grep error server_logs.txt` |
| `|` | Send output to another command | `ls | grep Q1` |
| `find` | Search files/directories | `find /home/analyst/projects` |
| `find -name` | Case-sensitive name search | `find . -name "*log*"` |
| `find -iname` | Case-insensitive name search | `find . -iname "*log*"` |
| `find -mtime` | Search by modified days | `find . -mtime -3` |
| `find -mmin` | Search by modified minutes | `find . -mmin -30` |

## Complete Lab Workflow

```bash
cd /home/analyst/logs
grep error server_logs.txt

cd /home/analyst/reports/users
ls | grep Q1
ls | grep access
```

## Key Concepts

- **Filtering:** selecting data that matches a condition
- **Standard output:** information returned by the shell
- **Standard input:** information received by a command
- **Pipe:** connects one command's output to another command's input
- **Search criteria:** conditions used by `find`

## Security Relevance

These tools help security analysts:

- Search large logs
- Locate suspicious events
- Find files with specific names
- Identify recently modified files
- Filter user/access reports
- Investigate malware or unauthorized changes

## Core Takeaway

```bash
grep
|
find
```

Use `grep` to search text, pipes to connect commands, and `find` to locate files or directories based on names, modification times, and other criteria.
