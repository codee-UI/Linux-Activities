# Linux User Management with `sudo` — Concise Summary

## Objective
Learn how to manage Linux users, groups, and file ownership safely using `sudo`.

Main commands:
- `sudo` — run a command with temporary elevated privileges
- `useradd` — create a user
- `usermod` — modify an existing user
- `userdel` — delete a user
- `groupdel` — delete a group
- `chown` — change file or directory ownership

## Why Use `sudo`

Direct root login is risky because the root account has unrestricted access. `sudo` is safer because it temporarily grants elevated privileges only when needed.

Use `sudo` carefully and only for commands that require administrative access.

## Authentication vs Authorization

- **Authentication** — verifies who a user is
- **Authorization** — determines what the user is allowed to access

## `useradd` — Create a User

```bash
sudo useradd fgarcia
```

Set a primary group:

```bash
sudo useradd -g security fgarcia
```

Set supplemental groups:

```bash
sudo useradd -G finance,admin fgarcia
```

| Option | Purpose |
|---|---|
| `-g` | Set primary group |
| `-G` | Set supplemental groups |

## `usermod` — Modify a User

Change primary group:

```bash
sudo usermod -g executive fgarcia
```

Add a supplemental group:

```bash
sudo usermod -a -G marketing fgarcia
```

Important: use `-a` with `-G` when adding a new supplemental group so existing groups are not replaced.

Other useful options:

| Option | Purpose |
|---|---|
| `-d` | Change home directory |
| `-l` | Change login name |
| `-L` | Lock account |

Example:

```bash
sudo usermod -d /home/garcia_f fgarcia
```

Lock an account:

```bash
sudo usermod -L fgarcia
```

## `userdel` — Delete a User

```bash
sudo userdel fgarcia
```

Delete the user and their home directory:

```bash
sudo userdel -r fgarcia
```

Use `-r` carefully because it deletes user files.

## `chown` — Change Ownership

Change file owner:

```bash
sudo chown fgarcia access.txt
```

Change group owner:

```bash
sudo chown :security access.txt
```

The colon before the group name identifies group ownership.

---

# Lab Scenario

A new employee named `researcher9` joins the organization.

The tasks are to:
1. Create the user
2. Assign the primary group
3. Transfer ownership of a project file
4. Add a secondary group
5. Delete the user when they leave
6. Remove the unused personal group

## Task 1 — Add `researcher9`

```bash
sudo useradd researcher9
```

Assign primary group:

```bash
sudo usermod -g research_team researcher9
```

Alternative:

```bash
sudo useradd researcher9 -g research_team
```

## Task 2 — Assign File Ownership

```bash
sudo chown researcher9 /home/researcher2/projects/project_r.txt
```

This makes `researcher9` the owner of `project_r.txt`.

## Task 3 — Add a Secondary Group

```bash
sudo usermod -a -G sales_team researcher9
```

- `-a` = append
- `-G` = supplemental group
- options are case-sensitive

The primary group remains `research_team`.

## Task 4 — Delete the User

```bash
sudo userdel researcher9
```

The lab may display:

```text
Userdel: Group researcher9 not removed because it is not the primary group of user researcher9.
```

This is expected.

Remove the unused group:

```bash
sudo groupdel researcher9
```

---

## Complete Lab Workflow

```bash
sudo useradd researcher9
sudo usermod -g research_team researcher9
sudo chown researcher9 /home/researcher2/projects/project_r.txt
sudo usermod -a -G sales_team researcher9
sudo userdel researcher9
sudo groupdel researcher9
```

## Command Summary

| Command | Purpose |
|---|---|
| `sudo` | Run a command with elevated privileges |
| `useradd` | Add a user |
| `usermod` | Modify a user |
| `userdel` | Delete a user |
| `groupdel` | Delete a group |
| `chown` | Change ownership |
| `-g` | Set primary group |
| `-G` | Set supplemental group(s) |
| `-a` | Append to supplemental groups |
| `-L` | Lock an account |
| `-r` | Remove a user's home directory with `userdel` |

## Security Relevance

These commands help security analysts:
- Control system access
- Add and remove authorized users
- Manage group membership
- Transfer file ownership
- Lock inactive accounts
- Remove unnecessary privileges
- Apply the principle of least privilege

## Core Takeaway

Use `sudo` only when elevated privileges are required.

The key account-management commands are:

```bash
useradd
usermod
userdel
chown
```

Together, they support secure management of authentication, authorization, group membership, and file ownership in Linux.
