# Ch10 — Lab: Managing Users and Groups (Real Lab)

**Lab:** `users-review` | **Date:** May 31, 2026 | **Result:** ✅ 9/9 PERFECT
**Lab URL:** `rol.redhat.com/rol/app/courses/rh124-10.0/pages/ch10s11`

← [Back to RH124](./README.md)

---

## Objectives
- Edit `/etc/login.defs` (PASS_MAX_DAYS=30)
- Create `consultants` group GID 35000
- Create consultant1/2/3 users in group
- Configure `/etc/sudoers.d/consultants`
- Set account expiration 90 days
- Force password change on first login

---

## Final Grade: 9/9 ✅

```
PASS  Verify consultants group has proper GID (35000)
PASS  Verify group membership
PASS  Verify sudo access for consultants
PASS  Verify password set for users
PASS  Verify password expiration
PASS  Verify account expiration
PASS  Verifying default password expiration on serverb
PASS  Verifying password change date
```

---

## Key Commands

```bash
vim /etc/login.defs          # Set PASS_MAX_DAYS=30
groupadd -g 35000 consultants
vim /etc/sudoers.d/consultants   # %consultants ALL=(ALL) ALL

useradd -G consultants consultant1
useradd -G consultants consultant2
useradd -G consultants consultant3

passwd consultant1/2/3

chage -E $(date -d "+90 days" +%F) consultant1
chage -E $(date -d "+90 days" +%F) consultant2
chage -E $(date -d "+90 days" +%F) consultant3

chage -d 0 consultant1/2/3
```

---

## Errors → Fixes Documented

| Error | Fix |
|-------|-----|
| Wrong GID (350000) | `groupdel consultants` → `groupadd -g 35000 consultants` |
| Date hardcoded | Use `$(date -d "+90 days" +%F)` command substitution |
| First grade: 7/9 | Fixed GID + date → **9/9** |

---

## Takeaway
The complete error → diagnosis → fix cycle is documented. First grade 7/9 → identified both errors → fixed GID with groupdel/groupadd → fixed date with `$()` substitution → **perfect 9/9**.

*Screenshot: [screenshots/RH124/ch10-users-review-lab.png](../screenshots/RH124/)*
