# Ch10 — Guided Exercise: Managing Local Groups

**Lab:** `users-group` | **Date:** May 31, 2026 | **Result:** ✅ PASS
**Time:** 00:09 → 00:19 | **Lab URL:** `rol.redhat.com/rol/app/courses/rh124-10.0/pages/ch10s08`

← [Back to RH124](./README.md)

---

## Objectives
- Create supplementary groups with `groupadd`
- Add users to groups with `usermod -aG`
- Verify membership with `id`
- Test sudo access using group membership

---

## Commands Used

```bash
lab start users-group
ssh servera → sudo -i

groupadd -g 30000 operators
groupadd admin
tail /etc/group         # verify operators:x:30000: and admin:x:30001:

usermod -aG operators operator1
usermod -aG operators operator2
usermod -aG operators operator3

id operator1            # groups=1003(operator1),30000(operators) ✅
id operator2            # groups=1004(operator2),30000(operators) ✅
id operator3            # groups=1005(operator3),30000(operators) ✅

usermod -aG admin sysadmin1
usermod -aG admin sysadmin2
usermod -aG admin sysadmin3

id sysadmin1            # groups=1006(sysadmin1),30001(admin) ✅

# Test: sysadmin1 reads restricted log
ssh sysadmin1@servera
tail /var/log/messages       # Permission denied ❌
sudo tail /var/log/messages  # Success ✅

exit → exit → exit
lab finish users-group
SUCCESS  Revoking administrative rights
SUCCESS  Removing operator/sysadmin users
SUCCESS  Removing operators and admin groups
```

---

## Critical: -aG vs -G

| Command | Effect |
|---------|--------|
| `usermod -aG group user` | ✅ Appends — safe |
| `usermod -G group user` | ⚠️ Replaces ALL supplementary groups |

---

## Takeaway
The `Permission denied → sudo success` sequence proved group-based access control in action. The `admin` group membership granted sudo privileges — not individual permissions. Same principle I apply in physical security: access by role, not by individual.

*Screenshot: [screenshots/RH124/ch10-users-group-guided.png](../screenshots/RH124/)*
