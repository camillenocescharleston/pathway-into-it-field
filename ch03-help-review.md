# Ch03 — Getting Help in Red Hat Linux

**Lab:** `help-review` | **Date:** May 9, 2026 | **Result:** ⚠️ 4/5 PASS

← [Back to RH124](./README.md)

---

## Objectives
- Use `man` pages to find command documentation
- Record system info: FQDN, SELinux mode, epoch time
- Print a man page to a PostScript printer
- Save findings to a task file

---

## Commands Used

```bash
student@workstation:~$ man -t bash | lpr -Pps
```

```bash
student@workstation:~$ lab grade help-review
PASS    Verifying that the lab file exists
FAIL    Verifying the FQDNS of the workstation machine
        - The file does not contain the expected FQDNS
PASS    Verifying the elapsed seconds
PASS    Verifying the current SELinux mode
PASS    Verifying the command for the manual page print
```

---

## Grade Analysis: 4/5

| Check | Result | Note |
|-------|--------|------|
| Lab file exists | ✅ PASS | `my_task.txt` created |
| FQDN correct | ❌ FAIL | Recorded `workstation` instead of full domain |
| Epoch seconds | ✅ PASS | |
| SELinux mode | ✅ PASS | `Enforcing` |
| man page print command | ✅ PASS | |

**The FAIL:** `hostname` returns short name. `hostname -f` returns the full FQDN. Always use `-f` when a full domain name is required.

---

## Key Concepts

| Tool | Purpose |
|------|---------|
| `man -t bash \| lpr -Pps` | Format + print bash man page |
| `hostname -f` | Full FQDN |
| `getenforce` | SELinux mode |
| `date +%s` | Unix epoch timestamp |

---

*Screenshot: [screenshots/RH124/ch03-help-review.png](../screenshots/RH124/)*
