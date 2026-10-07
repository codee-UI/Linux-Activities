# Linux APT Lab — Concise Task Summary

## Objective

Practice using the **APT package manager** and `sudo` in a Debian-based Linux Bash shell to install, remove, reinstall, and verify security tools.

The two applications used are:

- **Nload** — monitors network traffic and bandwidth usage
- **tcpdump** — captures and analyzes network traffic

---

## Task 1 — Confirm APT Is Installed

Run:

```bash
apt
```

### What to check

If APT is installed, it displays version and usage information.

### Purpose

Confirm that the system can use APT to manage software packages.

---

## Task 2 — Install and Remove Nload

### Install Nload

```bash
sudo apt install nload
```

Press **Enter** when prompted to continue.

### Verify installation

```bash
nload -h
```

You should see Nload version and usage information.

### Remove Nload

```bash
sudo apt remove nload
```

Press **Enter** when prompted.

### Verify removal

```bash
nload -h
```

Expected result:

```text
-bash: /usr/bin/nload: No such file or directory
```

### Purpose

Learn how to install, verify, uninstall, and confirm removal of a Linux application.

---

## Task 3 — Install tcpdump

Run:

```bash
sudo apt install tcpdump
```

### Purpose

Install a command-line network packet capture and analysis tool.

---

## Task 4 — List Installed Applications

Run:

```bash
apt list --installed
```

Look for:

```text
tcpdump
```

At this stage, `nload` should not appear because it was removed earlier.

### Purpose

Verify which software packages are currently installed.

---

## Task 5 — Reinstall Nload

Run:

```bash
sudo apt install nload
```

Then verify installed packages again:

```bash
apt list --installed
```

Confirm that both:

```text
nload
tcpdump
```

are installed.

---

## Command Summary

| Task | Command | Purpose |
|---|---|---|
| Check APT | `apt` | Confirm package manager is available |
| Install Nload | `sudo apt install nload` | Install Nload |
| Verify Nload | `nload -h` | Confirm Nload works |
| Remove Nload | `sudo apt remove nload` | Uninstall Nload |
| Verify removal | `nload -h` | Confirm Nload is gone |
| Install tcpdump | `sudo apt install tcpdump` | Install packet capture tool |
| List packages | `apt list --installed` | Show installed software |
| Reinstall Nload | `sudo apt install nload` | Install Nload again |

---

## Key Concepts

### APT
**Advanced Package Tool (APT)** is the package manager used in this Debian-based Linux lab.

### sudo
`sudo` runs a command with elevated privileges. It is required here because installing or removing software changes the system.

### Dependencies
When APT installs a package, it may also install additional software required by that package.

### Verification
Always verify that software was installed or removed correctly rather than assuming the command succeeded.

---

## Final Expected State

At the end of the lab:

- APT is available
- `tcpdump` is installed
- `nload` is installed

You should now know how to:

- Install packages
- Remove packages
- Verify installations
- List installed applications

---

## Core Takeaway

The main skill from this lab is **Linux software package management using APT**, an important skill for security analysts who need to install and maintain security tools in Linux environments.
