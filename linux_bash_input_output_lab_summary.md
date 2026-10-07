# Linux Bash Input/Output Lab — Concise Task Summary

## Objective
Practice basic Bash shell input/output using:
- `echo` — display text
- `expr` — perform integer calculations
- `clear` — clear the terminal

## Task 1 — Use `echo`

```bash
echo hello
echo "hello"
echo "Your Name"
```

Expected output is the text you provide.

**Purpose:** Understand that the command is the **input** and the returned text is the **output**.

## Task 2 — Use `expr`

Subtract alerts requiring action from total alerts:

```bash
expr 32 - 8
```

Output:

```text
24
```

Calculate yearly login attempts:

```bash
expr 3500 \* 12
```

Output:

```text
42000
```

### Important rules
- Put spaces between numbers and operators.
- `expr` performs integer calculations only.
- Operators: `+`, `-`, `/`, `*`

Examples:

```bash
expr 25 + 15
expr 10 - 3
expr 20 / 4
expr 5 \* 6
```

## Task 3 — Clear the Shell

```bash
clear
```

**Purpose:** Remove previous visible commands/output and return to a clean terminal screen.

## Optional Practice

```bash
echo "Cybersecurity Lab"
expr 100 / 3
```

Because `expr` uses integer arithmetic, `100 / 3` returns:

```text
33
```

## Command Summary

| Command | Purpose | Example |
|---|---|---|
| `echo` | Display text | `echo "hello"` |
| `expr` | Perform integer calculations | `expr 32 - 8` |
| `clear` | Clear terminal output | `clear` |

## Key Concepts

- **Input:** command entered into the shell
- **Output:** result returned by the shell
- **Error message:** response returned when a command cannot be processed correctly

## Final Skills

After this lab, you should be able to:

- Enter commands in Bash
- Recognize input and output
- Display text using `echo`
- Perform basic calculations using `expr`
- Clear the terminal using `clear`
- Understand why spacing matters in shell expressions

## Core Takeaway

This lab teaches how the **Bash shell receives input and returns output**, which is a foundation for more advanced Linux and cybersecurity command-line work.
