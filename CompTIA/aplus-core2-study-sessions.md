# CompTIA A+ Core 2 (220-1102) — Study Sessions Log

**Exam Date:** May 25, 2026
**Study Period:** April 21 – May 25, 2026

← [Back to CompTIA](./README.md)

---

## Session Overview

| Session | Date | Topic | Score |
|---------|------|-------|-------|
| Week 1 Day 2 | Apr 21, 2026 | Linux commands + permissions | 11/23 total |
| Weak Areas Review | Apr 25, 2026 | Linux, macOS, Windows disk tools | Full review |
| Practice Questions | Apr 27, 2026 | Mixed domains | 11/15 (73%) |
| Command Line Hands-On | May 30, 2026 | Windows CMD + Kali Linux | Practical |

---

## Week 1 Day 2 — Linux Commands & Permissions

### Commands Drilled

```bash
grep "keyword" filename.txt
cp source.txt destination.txt
rm -r directoryname/
pwd
ps aux
chown owner:group filename
chmod 755 filename
```

### Quiz Scores

| Round | Score |
|-------|-------|
| Round 1 | 1.5/5 |
| Round 2 | Improved |
| Flash drill | 3/3 ✅ |
| **Total** | **11/23** |

### chmod Math

| Value | Permissions |
|-------|-------------|
| 7 | rwx |
| 6 | rw- |
| 5 | r-x |
| 4 | r-- |
| 0 | --- |

---

## Weak Areas Review — Apr 25

### Linux Commands

| Command | Use |
|---------|-----|
| `ls -la` | List ALL files including hidden |
| `chmod 755 file` | rwxr-xr-x |
| `chmod 644 file` | rw-r--r-- |
| `chown user:group file` | Change ownership |
| `ps aux` | All running processes |
| `whoami` | Current username |

### macOS Boot Indicators

| Key/Indicator | Meaning |
|---------------|---------|
| Apple logo + progress | Normal boot |
| Circle with slash | Incompatible OS |
| Folder with ? | Boot disk not found |
| `Cmd+R` | Recovery Mode |
| `Shift` | Safe Mode |

### Windows Disk Tools

| Tool | Command | Purpose |
|------|---------|---------|
| Check Disk | `chkdsk C: /f /r` | Scan + fix errors |
| Disk Part | `diskpart` | Partition CLI |
| SFC | `sfc /scannow` | Repair system files |
| DISM | `DISM /Online /Cleanup-Image /RestoreHealth` | Repair image |

---

## Practice Questions — Apr 27

### Scores

| Round | Score | % |
|-------|-------|---|
| Round 1 | 4/5 | 80% |
| Round 2 | 4/5 | 80% |
| Round 3 | 3/5 | 60% |
| **Total** | **11/15** | **73%** |

### Weak Areas Flagged

| Topic | Correct Answer |
|-------|----------------|
| `chkdsk` on locked drive | Schedule with `/f`, reboot |
| Local Security Policy | `secpol.msc` → Account Policies |
| AppLocker vs UAC | AppLocker=restrict software, UAC=elevate |
| Domain join | Need Domain Admin credentials |

---

## Command Line Hands-On — May 30

### Windows CMD

```cmd
netstat     # active network connections
chkdsk      # disk health
```

### Kali Linux

```bash
whoami          # kali
hostname        # kali
hostname -I     # 10.0.2.15
ip addr show    # full NIC details
```

---

## Kali Linux VM — Real Troubleshooting

**Problem:** Forgotten root password
**Solution:** GRUB Single-User Mode

```bash
# At boot → Shift → GRUB menu → recovery mode
passwd root     # set new password
reboot
cat /etc/passwd # find username if forgotten
```

---

## Cumulative Weak Areas

| Topic | Status |
|-------|--------|
| Linux permissions / chmod | Improved ✅ |
| chkdsk on locked drives | Reviewed ✅ |
| AppLocker vs UAC | Reviewed ✅ |
| Local Security Policy | Reviewed ✅ |
| Domain join credentials | Reviewed ✅ |
| macOS boot indicators | Strong ✅ |

---

*Last updated: May 30, 2026*
