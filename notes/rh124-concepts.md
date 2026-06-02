# RH124 — Core Concepts & Study Notes

← [Back to main portfolio](../README.md)

*This file grows alongside the labs — theory connected to practice.*

---

## Chapter 2 — The Bash Shell

| Concept | Notes |
|---------|-------|
| Shell | Program that interprets commands — Bash is default on RHEL |
| Prompt | `[user@host dir]$` = regular user / `#` = root |
| `date +FORMAT` | `%R`=HH:MM, `%F`=YYYY-MM-DD, `%s`=epoch |

---

## Chapter 3 — Getting Help

| Tool | Use |
|------|-----|
| `man command` | Manual pages |
| `man -t cmd \| lpr -P` | Print man page |
| `hostname -f` | **Full FQDN** |
| `getenforce` | SELinux mode |
| `date +%s` | Unix epoch timestamp |

---

## Chapter 7 — File Permissions

```
-rwxr-xr--.
│└┬┘└┬┘└┬┘└── SELinux context
│ │  │  └── Others permissions
│ │  └───── Group permissions
│ └──────── Owner permissions
└────────── File type
```

| Value | Permissions |
|-------|-------------|
| 7 | rwx |
| 6 | rw- |
| 5 | r-x |
| 4 | r-- |
| 0 | --- |

---

## Chapter 8 — Vim Editor

| Mode | Enter | Exit |
|------|-------|------|
| Normal | `Esc` | default |
| Insert | `i/a/o` | `Esc` |
| Command | `:` | Enter |

Key commands: `:w` save, `:q` quit, `:wq` save+quit, `:q!` force quit, `dd` delete line, `u` undo

---

## Chapter 9 — I/O Redirection

| Operator | Meaning |
|----------|---------|
| `>` | Redirect stdout — **overwrites** |
| `>>` | Redirect stdout — **appends** |
| `2>` | Redirect stderr |
| `&>` | Both stdout and stderr |
| `\|` | Pipe |
| `tee` | Write to stdout AND file |
| `tee -a` | Append |

---

## Chapter 10 — Users and Groups

### sudo vs su

| Command | Requires | Use |
|---------|----------|-----|
| `sudo cmd` | Your password | Run as root |
| `sudo -i` | Your password | Full root shell |
| `su -` | Root password | Full root (old-school) |

### useradd workflow

```
# useradd username
   ↓ reads /etc/login.defs
   ↓ writes /etc/passwd + /etc/group
   ↓ creates /home/username
   ↓ copies /etc/skel files
```

### chage Quick Reference

| Command | Purpose |
|---------|---------|
| `chage -M 90 user` | Max 90 days |
| `chage -d 0 user` | Force change next login |
| `chage -E YYYY-MM-DD user` | Account expiration |
| `chage -l user` | List all settings |

### usermod Options

| Flag | Purpose |
|------|---------|
| `-aG group user` | Append to group (safe) |
| `-G group user` | Replace groups (dangerous!) |
| `-L user` | Lock account |
| `-U user` | Unlock account |
| `-c "Name" user` | Set comment |

---

## Chapter 11 — File Permissions

### Special Permissions

| Permission | Set with | Effect on Directory |
|-----------|----------|---------------------|
| setgid | `chmod g+s` or `2xxx` | New files inherit group |
| sticky | `chmod +t` or `1xxx` | Only owner can delete |

### chmod 3770 — Collaborative Directory

```
chmod 3770 /shared
3 = setgid(2) + sticky(1)
7 = owner rwx
7 = group rwx
0 = others --- (blocked completely)
```

### umask

| umask | Files | Dirs |
|-------|-------|------|
| 022 (default) | 644 | 755 |
| 007 | 660 | 770 |
| 077 | 600 | 700 |

### Directory vs File Permissions

| Permission | On FILE | On DIRECTORY |
|-----------|---------|--------------|
| `r` | Read | List contents |
| `w` | Modify | Create/delete files |
| `x` | Execute | Enter (cd) |

**Delete requires `w` on the DIRECTORY, not the file!**

---

## Chapter 12 — RPM and DNF

### rpm Query Options

| Option | Purpose |
|--------|---------|
| `-qf FILE` | Which package owns FILE? |
| `-ql` | List all files |
| `-qc` | Config files only |
| `-qd` | Documentation only |
| `-qi` | Package info |
| `--scripts` | Install/uninstall scripts |
| `--changelog` | Full changelog |
| `-p FILE.rpm` | Query uninstalled RPM |

### rpm2cpio

```bash
rpm2cpio file.rpm | cpio -tv    # list contents
rpm2cpio file.rpm | cpio -idv   # extract to disk
```

### DNF Commands

| Command | Purpose |
|---------|---------|
| `dnf search keyword` | Search |
| `dnf install package` | Install + deps |
| `dnf remove package` | Remove |
| `dnf update` | Update all |
| `dnf history` | Transaction history |
| `dnf provides /path` | Which package provides file? |

---

## Chapter 11 — File Permissions Quiz (6/6 ✅)

**Golden Rules:**
- Delete a file → requires `w` on the **DIRECTORY**
- Enter a directory → requires `x` on the directory
- List a directory → requires `r` on the directory

---

*Updated: June 1, 2026*
