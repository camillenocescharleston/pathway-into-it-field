# Ch12 — Guided Exercise: Install and Update Packages with DNF

**Lab:** `software-dnf` | **Date:** Jun 1, 2026 | **Result:** 🔄 In Progress

← [Back to RH124](./README.md)

---

## Objectives
- Find, install, and remove packages with DNF
- Install packages with automatic dependency resolution

---

## Commands Used So Far

```bash
lab start software-dnf
ssh servera → sudo -i

nepa                    # TYPO: nmap
nmap                    # bash: nmap: command not found ✅ confirmed not installed

nmap dnf search nmap    # TYPO: ran nmap before dnf
dnf search nmap         # ✅ correct
# Name Exactly Matched: nmap.x86_64 - Network exploration tool
# Name & Summary Matched: nmap-ncat.x86_64 - Nmap's Netcat replacement
```

---

## DNF Command Reference

| Command | Purpose |
|---------|---------|
| `dnf search keyword` | Search by name/summary |
| `dnf info package` | Detailed info |
| `dnf install package` | Install + dependencies |
| `dnf remove package` | Remove + dependents |
| `dnf update` | Update all packages |
| `dnf list installed` | List installed |
| `dnf history` | Transaction history |
| `dnf provides /path` | Which package provides file? |

## DNF vs RPM

| Feature | rpm | dnf |
|---------|-----|-----|
| Install single file | ✅ | ✅ |
| Auto-resolve dependencies | ❌ | ✅ |
| Search repositories | ❌ | ✅ |
| Update all packages | ❌ | ✅ |

---

*Screenshot: [screenshots/RH124/ch12-software-dnf-guided.png](../screenshots/RH124/)*
