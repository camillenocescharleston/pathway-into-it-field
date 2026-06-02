# Ch10 — Lab 08: Manage Local User Accounts

**Lab:** `users-user` | **Date:** May 30, 2026 | **Result:** ✅ PASS
**Time:** 22:24 → 22:37 | **Lab URL:** `rol.redhat.com/rol/app/courses/rh124-10.0/pages/ch10`

← [Back to RH124](./README.md)

---

## Objectives
- Create local user accounts with `useradd`
- Set passwords with `passwd`
- Modify accounts with `usermod`
- Delete users with `userdel -r`
- Verify with `/etc/passwd` and `ls -l /home`

---

## Commands Used

```bash
lab start users-user
ssh servera → sudo -i

useradd operator1
tail /etc/passwd        # verify operator1:x:1003:1003:...
passwd operator1        # BAD PASSWORD warning — root overrides

useradd operator2
passwd operator2

usermod -c "Operator One" operator1
usermode -c ...          # TYPO: usermode vs usermod
usermod -c "Operator Two" operator2
tail /etc/passwd        # verify comments applied

userdel -r operator3    # delete user + home dir
tail /etc/passwd        # verify gone
ls -l /home             # verify home dir gone

exit → exit
lab finish users-user
SUCCESS  Removing lab users
```

---

## Authentic Errors

| Error | Lesson |
|-------|--------|
| `$ -a` | Wait for prompt before typing |
| `password operator1` | Command is `passwd` not `password` |
| `passwd operator1s1` | Verify username spelling |
| `usermode` | Command is `usermod` not `usermode` |

---

## /etc/passwd Format

```
operator1:x:1003:1003:Operator One:/home/operator1:/bin/bash
username  pw  UID  GID   comment        home dir      shell
```

---

*Screenshot: [screenshots/RH124/ch10-users-user.png](../screenshots/RH124/)*
