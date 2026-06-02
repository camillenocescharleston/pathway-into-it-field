# Ch11 — Guided Exercise: Managing File Permissions from the CLI

**Lab:** `perms-cli` | **Date:** May 31, 2026 | **Result:** ✅ PASS

← [Back to RH124](./README.md)

---

## Objectives
- Create directories with specific permissions
- Use `chmod` numerically and symbolically
- Understand directory vs file permission effects

---

## Commands Used

```bash
# As student — fails
mkdir -pv /data         # Permission denied

# As root
mkdir -pv /data
ls -ld /data            # drwxr-xr-x (755 default)

chmod 000 /data
ls -ld /data            # d---------- (000)

cd data                 # TYPO: missing slash
cd /data                # ✅ absolute path

touch root.1
ls -l                   # -rw-r--r-- root root root.1

chmod 001 /data         # others execute only
chmod 005 /data         # others read+execute

lab finish perms-cli
SUCCESS  Removing consultant users and group
```

---

## chmod Effects on Directories

| chmod | String | Others can... |
|-------|--------|---------------|
| `755` | rwxr-xr-x | list + enter |
| `000` | ---------- | nothing |
| `001` | ---------x | enter only |
| `005` | -----r-x | list + enter |

## Directory vs File Permissions

| Permission | On FILE | On DIRECTORY |
|-----------|---------|--------------|
| `r` | Read contents | List (`ls`) |
| `w` | Modify file | Create/delete files |
| `x` | Execute | Enter (`cd`) |

---

## Takeaway
Root bypasses `000` permissions — root always wins. Regular users would be completely blocked.

*Screenshot: [screenshots/RH124/ch11-perms-cli-guided.png](../screenshots/RH124/)*
