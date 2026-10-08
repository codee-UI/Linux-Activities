# Linux File and Directory Management — Concise Summary

## Objective

Learn how to create, remove, move, copy, and edit files and directories in Linux using Bash.

Main commands:

- `mkdir` — create a directory
- `rmdir` — remove an empty directory
- `touch` — create an empty file
- `rm` — remove a file
- `mv` — move or rename a file/directory
- `cp` — copy a file/directory
- `nano` — edit text files
- `>` — overwrite a file
- `>>` — append to a file

---

## Core Commands

### Create a directory

```bash
mkdir network
```

Verify:

```bash
ls
```

### Remove an empty directory

```bash
rmdir network
```

### Create an empty file

```bash
touch permissions.txt
```

### Remove a file

```bash
rm permissions.txt
```

Use `rm` carefully because deleted files may be difficult to recover.

### Move a file

```bash
mv permissions.txt /home/analyst/logs
```

### Rename a file

```bash
mv permissions.txt perm.txt
```

### Copy a file

```bash
cp permissions.txt /home/analyst/logs
```

Unlike `mv`, the original file remains in place.

---

## Nano Text Editor

Open or create a file:

```bash
nano tasks.txt
```

Useful shortcuts:

| Shortcut | Action |
|---|---|
| `Ctrl + O` | Save |
| `Ctrl + X` | Exit |

In the web lab, save and exit with:

```text
Ctrl + X
Y
Enter
```

---

## Output Redirection

Overwrite a file:

```bash
echo "time" > permissions.txt
```

Append to a file:

```bash
echo "last updated date" >> permissions.txt
```

- `>` replaces existing contents.
- `>>` adds content to the end.
- Both can create a file if it does not already exist.

---

# Lab Scenario

Initial structure:

```text
home
└── analyst
    ├── notes
    │   ├── Q3patches.txt
    │   └── tempnotes.txt
    ├── reports
    │   ├── Q1patches.txt
    │   └── Q2patches.txt
    └── temp
```

Target structure:

```text
home
└── analyst
    ├── logs
    ├── notes
    │   └── tasks.txt
    └── reports
        ├── Q1patches.txt
        ├── Q2patches.txt
        └── Q3patches.txt
```

---

## Task 1 — Create `logs`

From `/home/analyst`:

```bash
mkdir logs
ls
```

Expected:

```text
logs notes reports temp
```

---

## Task 2 — Remove `temp`

```bash
rmdir temp
ls
```

Expected:

```text
logs notes reports
```

---

## Task 3 — Move `Q3patches.txt`

```bash
cd /home/analyst/notes
mv Q3patches.txt /home/analyst/reports/
ls /home/analyst/reports
```

Expected:

```text
Q1patches.txt Q2patches.txt Q3patches.txt
```

---

## Task 4 — Remove `tempnotes.txt`

```bash
rm tempnotes.txt
ls
```

The `notes` directory should now be empty.

---

## Task 5 — Create `tasks.txt`

```bash
touch tasks.txt
ls
```

Expected:

```text
tasks.txt
```

---

## Task 6 — Edit `tasks.txt`

Open the file:

```bash
nano tasks.txt
```

Add:

```text
Completed tasks
1. Managed file structure in /home/analyst
```

Save and exit:

```text
Ctrl + X
Y
Enter
```

Clear the terminal:

```bash
clear
```

Verify:

```bash
cat tasks.txt
```

Expected:

```text
Completed tasks
1. Managed file structure in /home/analyst
```

---

## Complete Lab Workflow

```bash
cd /home/analyst

mkdir logs
ls

rmdir temp
ls

cd /home/analyst/notes

mv Q3patches.txt /home/analyst/reports/
ls /home/analyst/reports

rm tempnotes.txt
ls

touch tasks.txt
ls

nano tasks.txt

clear
cat tasks.txt
```

---

## Command Summary

| Command | Purpose |
|---|---|
| `mkdir` | Create directory |
| `rmdir` | Remove empty directory |
| `touch` | Create empty file |
| `rm` | Remove file |
| `mv` | Move or rename |
| `cp` | Copy |
| `nano` | Edit a text file |
| `>` | Overwrite file with output |
| `>>` | Append output to file |
| `ls` | Verify files/directories |
| `cat` | Display file contents |
| `clear` | Clear terminal |

---

## Security Relevance

These skills help security analysts:

- Organize logs and reports
- Remove obsolete files
- Move reports to correct locations
- Maintain clean directory structures
- Document completed work
- Edit notes and configuration files
- Manage security-related data from the command line

---

## Core Takeaway

The essential Linux file-management commands are:

```bash
mkdir
rmdir
touch
rm
mv
cp
nano
```

Together, they allow you to create, organize, move, remove, copy, and edit files and directories efficiently.
