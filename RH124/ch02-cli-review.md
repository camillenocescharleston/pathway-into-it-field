# Ch02 — Accessing the Command Line

**Lab:** `cli-review` | **Date:** April 20, 2026 | **Result:** ✅ PASS

← [Back to RH124](./README.md)

---

## Objectives
- Navigate the Bash shell environment
- Use basic command-line syntax, options, and arguments
- Read command help output (`--help`, `--version`)
- Work with the `date` command and format strings

---

## Commands Used

```bash
# Display current time in HH:MM format
student@workstation:~$ date +%R
23:01
```

| Part | Meaning |
|------|---------|
| `date` | Print system date/time |
| `+%R` | Format string — 24-hour time HH:MM |

```bash
student@workstation:~$ lab grade cli-review
Running: lab grade cli-review
PASS    No items to evaluate
        Check completed: no items found to evaluate.
```

```bash
student@workstation:~$ lab finish cli-review
Running: lab finish cli-review
SUCCESS  Removing temporary files
student@workstation:~$
```

---

## Command Reference

| # | Command | Purpose |
|---|---------|---------|
| 1 | `date +%R` | Display current time (HH:MM) |
| 2 | `lab grade cli-review` | Auto-grade lab |
| 3 | `lab finish cli-review` | Teardown environment |

---

## Key Concepts

| Concept | Notes |
|---------|-------|
| `date` format strings | `%R`=time, `%F`=date, `%s`=epoch seconds |
| `--help` | Usage info for any command |
| `--version` | Installed version info |
| Bash `case` structure | `case $1 in --help) ... --version) ...` |

---

## Takeaway
First lab — getting comfortable with the ROL/Guacamole terminal environment and the `lab` command workflow. The `date +%R` format string is a small but important detail: Linux date formatting uses `%` codes, not fixed syntax. That pattern repeats everywhere in scripting.

---

*Screenshot: [screenshots/RH124/ch02-cli-review.png](../screenshots/RH124/)*
