# Ch10 — Guided Exercise: Manage User Passwords

**Lab:** `users-password` | **Date:** May 31, 2026 | **Result:** ✅ PASS
**Time:** 00:26 → 00:47 | **Lab URL:** `rol.redhat.com/rol/app/courses/rh124-10.0/pages/ch10`

← [Back to RH124](./README.md)

---

## Objectives
- Lock/unlock accounts with `usermod -L` / `usermod -U`
- Set password aging with `chage`
- Force password change on next login: `chage -d 0`
- Set account expiration: `chage -E`

---

## Commands Used

```bash
lab start users-password
ssh servera

sudo usermod -L -e 1 operator1     # Lock + expire account
su -operator1                       # TYPO: missing space
su - operator1                      # Password: Authentication failure ✅ locked

sudo usermod -U -e '' operator1     # Unlock + clear expiration
su - operator1                      # 2 failed login attempts since last login (audit log!)

# operator1 not in sudoers — cannot sudo to fix own account
exit

sudo -i
chage -M 90 operator1              # 90 day max password age
chage -1 operator1                  # TYPO: -1 vs -l → shows help
chage -l operator1                  # ✅ List aging info
Password expires    : May 31, 2026
Maximum days        : 90
Warning days        : 7

chage -d 0 operator1               # Force change on next login
chage -E 2026-11-10 operator1      # Set account expiration date
chage -l operator1 | grep "Account expires"
Account expires : Nov 10, 2026 ✅

exit → exit
lab finish users-password
SUCCESS  Removing lab user
SUCCESS  Restore the /etc/login.defs file
```

---

## chage Quick Reference

| Command | Purpose |
|---------|---------|
| `chage -M 90 user` | Max 90 days |
| `chage -m 0 user` | No minimum |
| `chage -W 7 user` | Warn 7 days before |
| `chage -d 0 user` | Force change at next login |
| `chage -E YYYY-MM-DD user` | Account expiration |
| `chage -l user` | List all settings |

---

## Authentic Errors

| Error | Lesson |
|-------|--------|
| `su -operator1` | Space required: `su - operator1` |
| `sudo usermode` | Command is `usermod` not `usermode` |
| `chage -1` | It's lowercase L not number 1 |
| `operator1 not in sudoers` | Can't grant yourself sudo |

---

*Screenshot: [screenshots/RH124/ch10-users-password-guided.png](../screenshots/RH124/)*
