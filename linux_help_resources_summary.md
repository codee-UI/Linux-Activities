# Linux Help Resources — Concise Summary

## Objective
Learn how to get help directly from the Linux command line and use trusted community resources when you need information about commands.

Main help tools:
- `man` — detailed manual pages
- `whatis` — one-line command description
- `apropos` — search command descriptions by keyword
- Unix & Linux Stack Exchange — community troubleshooting resource

## Linux Community

Linux has a large global user community.

A useful resource is **Unix & Linux Stack Exchange**, where users ask and answer Linux troubleshooting questions.

Use community resources when:
- You encounter an unfamiliar error
- You need troubleshooting ideas
- You want examples from other Linux users
- Built-in help does not fully answer your question

## `man` — Detailed Help

The `man` command displays a command's manual page.

```bash
man chown
```

Another example:

```bash
man cat
```

Useful keys inside a man page:

| Key | Action |
|---|---|
| `Enter` | Move down one line |
| `Space` | Move forward one page |
| `q` | Quit |

## `whatis` — Quick Description

`whatis` displays a short one-line description of a command.

```bash
whatis nano
```

Use it when you only need a quick reminder.

## `apropos` — Search by Keyword

`apropos` searches manual-page descriptions.

```bash
apropos editor
```

Search for multiple words:

```bash
apropos -a graph editor
```

The `-a` option returns entries matching all specified keywords.

# Lab Tasks

## Task 1 — Learn More About Commands

Quick description of `cat`:

```bash
whatis cat
```

Answer:

```text
concatenate files
```

Detailed help:

```bash
man cat
```

Option that numbers all output lines:

```text
-n, --number
```

Find the command that displays the first part of a file:

```bash
apropos -a first part file
```

Answer:

```text
head
```

## Task 2 — Explore `useradd`

```bash
man useradd
```

Option for setting an account expiration date:

```text
-e
```

## Task 3 — Compare `rm` and `rmdir`

```bash
whatis rm
whatis rmdir
```

Answer: `rmdir` removes empty directories.

## Task 4 — Find the Command to Create a Group

```bash
apropos -a create new group
```

Answer:

```text
groupadd
```

## Complete Lab Workflow

```bash
whatis cat
man cat
apropos -a first part file
man useradd
whatis rm
whatis rmdir
apropos -a create new group
```

## Lab Answers

| Question | Answer |
|---|---|
| First two words from `whatis cat` | `concatenate files` |
| Option to number all `cat` output lines | `-n, --number` |
| Command that shows the first part of a file | `head` |
| `useradd` option for expiration date | `-e` |
| Command that removes only empty directories | `rmdir` |
| Command used to create a new group | `groupadd` |

## Command Summary

| Command | Purpose |
|---|---|
| `man COMMAND` | Show detailed manual page |
| `whatis COMMAND` | Show a short description |
| `apropos KEYWORD` | Search man-page descriptions |
| `apropos -a WORD1 WORD2` | Search for entries matching all keywords |

## When to Use Each Tool

Use `whatis` when you need a **quick reminder**.

Use `man` when you need **detailed syntax, options, and usage**.

Use `apropos` when you **know the task but not the command name**.

## Security Relevance

These tools help security analysts:
- Verify command syntax before running it
- Discover command options
- Reduce mistakes in administrative tasks
- Learn unfamiliar commands
- Troubleshoot from the command line
- Continue learning Linux independently

## Core Takeaway

```text
Know the command, need details   → man
Know the command, need reminder  → whatis
Know the task, not the command   → apropos
```
