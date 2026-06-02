# Ch12 — Guided Exercise: Investigate an RPM Software Package

**Lab:** RPM Investigation | **Date:** Jun 1, 2026 | **Result:** ✅ PASS

← [Back to RH124](./README.md)

---

## Objectives
- Use `rpm` query options to investigate packages
- Find which package owns a file
- View scripts, changelogs, and file lists
- Extract RPM contents with `rpm2cpio`
- Install a local RPM with `rpm -ivh`

---

## Commands Used

```bash
rpm -qf /etc/yum.repos.d           # which package owns this?
rpm -q dnf                          # installed version
rpm -q kernel | sort                # kernel versions (alphabetic)
rpm -q kernel | rpmsort             # kernel versions (version-aware)
rpm -ql dnf                         # all files in package
rpm -qc openssh-clients             # config files only
rpm -qd openssh-clients             # documentation only
rpm -q --scripts openssh-server     # install/uninstall scripts
rpm -q --changelog audit            # full changelog

# Uninstalled RPM file investigation
rpm -qip rhcsa-script-1.0.0-1.noarch.rpm    # info before install
rpm -qp --scripts rhcsa-script-*.rpm         # scripts before install

rmp2cpio rhcsa-script-*.rpm | cpio -tv      # TYPO: rmp vs rpm
rpm2cpio rhcsa-script-*.rpm | cpio -tv      # list contents ✅
rpm2cpio rhcsa-script-*.rpm | cpio -idv     # extract to disk

sudo rpm -ivh rhcsa-script-1.0.0-1.noarch.rpm
# Verifying [100%] → Preparing [100%] → Installing [100%]

ssh servera  # Reconnect — ASCII art MOTD appeared!
# Package's postinstall script replaced /etc/motd ✅
```

---

## rpm Query Options

| Option | Purpose |
|--------|---------|
| `-qf FILE` | Which package owns FILE? |
| `-ql` | List all files |
| `-qc` | Config files only |
| `-qd` | Documentation only |
| `-qi` | Package info |
| `--scripts` | Install/uninstall scripts |
| `--changelog` | Full changelog |
| `-p FILE.rpm` | Query uninstalled RPM file |

## rpm2cpio Pipeline

| Command | Action |
|---------|--------|
| `rpm2cpio file.rpm \| cpio -tv` | List contents |
| `rpm2cpio file.rpm \| cpio -idv` | Extract to disk |

---

## Takeaway
The ASCII art MOTD appearing after install proved: inspect scripts BEFORE installing → know exactly what will happen → install → confirm. That's the professional workflow. Never install an RPM without checking its scripts first.

*Screenshot: [screenshots/RH124/ch12-rpm-investigation-guided.png](../screenshots/RH124/)*
