# File Permissions in Linux

## Project Description

The research team needs file and directory permissions in `/home/researcher2/projects` to match the organization’s authorization requirements. I used Linux commands to inspect existing permissions, identify excessive access, and apply the principle of least privilege. I verified hidden files, changed file permissions with `chmod`, and restricted access to the `drafts` directory.

---

## Check File and Directory Details

To display all files, including hidden files, together with detailed permission information, I used:

```bash
cd /home/researcher2/projects
ls -la
```

`ls -la` combines:

- `-l` — detailed listing, including permissions, owner, group, size, and modification time
- `-a` — includes hidden files whose names begin with `.`

### Current Permissions

| Item | Type | Permission String | User | Group | Other |
|---|---|---|---|---|---|
| `project_k.txt` | File | `-rw-rw-rw-` | read, write | read, write | read, write |
| `project_m.txt` | File | `-rw-r-----` | read, write | read | none |
| `project_r.txt` | File | `-rw-rw-r--` | read, write | read, write | read |
| `project_t.txt` | File | `-rw-rw-r--` | read, write | read, write | read |
| `.project_x.txt` | Hidden file | `-rw--w----` | read, write | write | none |
| `drafts` | Directory | `drwx--x---` | read, write, execute | execute | none |

The files belong to user `researcher2` and group `research_team`. The hidden file is `.project_x.txt`.

---

## Describe the Permissions String

Linux represents permissions using a **10-character string**.

Example:

```text
-rw-rw-r--
```

This is the permission string for `project_t.txt`.

### Character Breakdown

| Characters | Meaning |
|---|---|
| 1st | File type: `-` = regular file, `d` = directory |
| 2nd–4th | User permissions |
| 5th–7th | Group permissions |
| 8th–10th | Other-user permissions |

Permission symbols:

- `r` = read
- `w` = write
- `x` = execute
- `-` = permission not granted

For `-rw-rw-r--`:

- **File type:** regular file
- **User:** read and write
- **Group:** read and write
- **Other:** read only
- **Execute:** not granted to anyone

---

## Change File Permissions

The organization does not allow other users to have write access to files.

The file that violates this requirement is:

```text
project_k.txt
```

Its original permissions are:

```text
-rw-rw-rw-
```

To remove write permission from `other`, I used:

```bash
chmod o-w project_k.txt
```

Then I verified the change:

```bash
ls -la
```

The updated permission string is:

```text
-rw-rw-r--
```

### Command Explanation

- `chmod` — changes file or directory permissions
- `o` — represents other users
- `-w` — removes write permission
- `project_k.txt` — target file

---

## Change File Permissions on a Hidden File

The archived hidden file:

```text
.project_x.txt
```

should not be writable by anyone. The user and group should both be able to read it.

Its original permissions are:

```text
-rw--w----
```

I used:

```bash
chmod u-w,g-w,g+r .project_x.txt
```

Then verified:

```bash
ls -la
```

The intended permission string becomes:

```text
-r--r-----
```

### Command Explanation

- `u-w` — removes write permission from the user
- `g-w` — removes write permission from the group
- `g+r` — adds read permission for the group
- `.project_x.txt` — the leading `.` identifies a hidden file

---

## Change Directory Permissions

Only the `researcher2` user should be able to access the `drafts` directory and its contents.

The original permissions are:

```text
drwx--x---
```

The group has execute permission, which allows access to the directory.

To remove this access, I used:

```bash
chmod g-x drafts
```

Then verified:

```bash
ls -la
```

The intended permission string becomes:

```text
drwx------
```

### Command Explanation

- `g` — represents the group
- `-x` — removes execute permission
- `drafts` — target directory

---

## Complete Command Sequence

```bash
cd /home/researcher2/projects

ls -la

chmod o-w project_k.txt

chmod u-w,g-w,g+r .project_x.txt

chmod g-x drafts

ls -la
```

---

## Before and After Summary

| Item | Before | Required Change | After |
|---|---|---|---|
| `project_k.txt` | `-rw-rw-rw-` | Remove other write | `-rw-rw-r--` |
| `.project_x.txt` | `-rw--w----` | Remove user/group write; add group read | `-r--r-----` |
| `drafts` | `drwx--x---` | Remove group execute | `drwx------` |

---

## Security Principle Applied

### Principle of Least Privilege

The **principle of least privilege** means users should receive only the minimum permissions necessary to perform their responsibilities.

In this activity:

- Unauthorized write access was removed from `project_k.txt`.
- The archived `.project_x.txt` file was changed to read-only for the authorized user and group.
- Group access to the confidential `drafts` directory was removed.

---

## Summary

I used `ls -la` to inspect file and directory permissions, including hidden files, in the research team’s projects directory. I interpreted Linux permission strings and used `chmod` to remove excessive file and directory access. The final permissions better align with the organization’s authorization requirements and the principle of least privilege.

---

## Suggested Screenshots for Portfolio

Include these if you revisit the lab:

1. `ls -la` showing original permissions
2. `chmod o-w project_k.txt` followed by `ls -la`
3. `chmod u-w,g-w,g+r .project_x.txt` followed by `ls -la`
4. `chmod g-x drafts` followed by `ls -la`

Show the terminal command and output only; avoid including unrelated lab instructions.

---

## Self-Assessment Checklist

- [x] Project description included
- [x] `ls -la` explained
- [x] Current permissions documented
- [x] 10-character permission string interpreted
- [x] `chmod` used on a regular file
- [x] Hidden-file permissions updated
- [x] Directory permissions updated
- [x] Final summary included
