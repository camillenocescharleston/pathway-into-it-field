# Ch11 — Lab: Control Access to Files (Real Lab)

**Lab:** `perms-review` | **Date:** May 31, 2026 | **Result:** ✅ 5/5 PERFECT

← [Back to RH124](./README.md)

---

## Final Grade: 5/5 ✅

```
PASS  Verifying permissions on /home/techdocs
PASS  Verifying the file structure
PASS  Verifying umask for dev1
PASS  Verifying umask for dev2
PASS  Verifying that dbadmin1 cannot edit /home/techdocs
```

---

## Objectives
- Create `techdocs` collaborative directory
- setgid: new files inherit `techdocs` group
- sticky bit: only owner can delete own files
- `dbadmin1` (not in techdocs) blocked completely
- Persistent umask for dev1 and dev2

---

## Commands Used

```bash
lab start perms-review   # creates techdocs group, dev1, dev2, dbadmin1

ssh serverb → sudo -i

mkdir /home/techdocs
chown :techdocs /home/techdocs
chmod 3770 /home/techdocs
ls -ld /home/techdocs
# drwxrws--T. 2 root techdocs → ✅ setgid(s) + sticky(T)

su - dev1
cd /home/techdocs
mkdir dev1
touch dev1/dev1.txt dev1/dev1.log dev1/dev1.cfg
exit

su - dev2
umask 007
echo "umask 007" >> ~/.bashrc
cd /home/techdocs
mkdir dev2
touch dev2/dev2.txt dev2/dev2.log dev2/dev2.cfg
exit

echo "umask 007" >> /home/dev1/.bashrc
grep umask /home/dev1/.bashrc  # verify ✅

exit → exit
lab grade perms-review   # 4/5 first attempt (dev1 umask wrong)
# Fix: already in .bashrc but needed re-grade
lab grade perms-review   # 5/5 ✅

lab finish perms-review
```

---

## chmod 3770 — The Collaborative Directory Formula

```
3 = setgid(2) + sticky(1)
7 = owner rwx
7 = group rwx
0 = others ---  ← blocks dbadmin1 completely
```

---

## Takeaway
`chmod 3770` in one command set up the entire collaborative directory — setgid ensures group inheritance, sticky bit ensures deletion protection, `others=0` blocks everyone not in the group. That's enterprise-grade access control from a single command.

*Screenshot: [screenshots/RH124/ch11-perms-review-lab.png](../screenshots/RH124/)*
