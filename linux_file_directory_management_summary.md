# Linux File and Directory Management — Concise Summary

## Objective

Learn to manage Linux files and directories using:

- `mkdir`
- `rmdir`
- `touch`
- `rm`
- `mv`
- `cp`
- `nano`
- `>`
- `>>`

---

## Core Commands

| Command | Purpose | Example |
|---|---|---|
| `mkdir` | Create a directory | `mkdir logs` |
| `rmdir` | Remove an empty directory | `rmdir temp` |
| `touch` | Create an empty file | `touch tasks.txt` |
| `rm` | Delete a file | `rm tempnotes.txt` |
| `mv` | Move or rename a file | `mv Q3patches.txt /home/analyst/reports` |
| `cp` | Copy a file | `cp file.txt /home/analyst/logs` |
| `nano` | Edit a text file | `nano tasks.txt` |
| `>` | Overwrite file contents | `echo "time" > file.txt` |
| `>>` | Append to file contents | `echo "update" >> file.txt` |

---

## Important Notes

- `rmdir` removes **empty directories only**.
- `rm` deletes files and should be used carefully.
- `mv` can both move and rename files.
- `cp` creates a copy while keeping the original.
- `>` overwrites existing contents.
- `>>` appends new contents.
- In `nano`, `Ctrl + O` saves and `Ctrl + X` exits.

---

## Lab Goal

Change this structure:

```text
/home/analyst
├── notes
│   ├── Q3patches.txt
│   └── tempnotes.txt
├── reports
│   ├── Q1patches.txt
│   └── Q2patches.txt
└── temp
```

into:

```text
/home/analyst
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

```bash
cd /home/analyst
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
mv Q3patches.txt /home/analyst/reports
ls /home/analyst/reports
```

Expected:

```text
Q1patches.txt
Q2patches.txt
Q3patches.txt
```

---

## Task 4 — Delete `tempnotes.txt`

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

Open:

```bash
nano tasks.txt
```

Add:

```text
Completed tasks
1. Managed file structure in /home/analyst
```

In the web lab:

1. Press `Ctrl + X`
2. Press `Y`
3. Press `Enter`

Then verify:

```bash
clear
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

cd notes
mv Q3patches.txt /home/analyst/reports
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

## Output Redirection

Append text:

```bash
echo "last updated date" >> permissions.txt
```

Overwrite the file:

```bash
echo "time" > permissions.txt
```

Difference:

```text
>   = overwrite
>>  = append
```

Use `>` carefully because previous file contents are replaced.

---

## Security Relevance

These commands help security analysts:

- Organize logs and reports
- Manage investigation files
- Move security evidence
- Delete obsolete files
- Create documentation
- Edit configuration or notes
- Maintain organized directory structures

---

## Core Takeaway

The main Linux file-management commands are:

```bash
mkdir
rmdir
touch
rm
mv
cp
nano
```

And for writing command output to files:

```bash
>
>>
```
