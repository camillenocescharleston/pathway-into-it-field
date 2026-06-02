# Ch11 — Guided Exercise: Default Permissions and Special Permissions

**Lab:** `perms-default` | **Date:** May 31, 2026 | **Result:** ✅ PASS

← [Back to RH124](./README.md)

---

## Objectives
- Create shared directory with automatic group ownership (setgid)
- Only file owner can delete files (sticky bit)
- Temporarily change umask

---

## Commands Used

```bash
# Create ops files as operator1
touch ops_file2.txt
ls -l ops_file{1,2}.txt
-rw-rw----. operator1 operators ops_file1.txt  (umask 007)
-rw-r--r--. operator1 operators ops_file2.txt  (umask 022)

# Switch to operator2 and try to delete operator1's file
su operator2
rm /tmp/operators/ops_file1.txt
rm: cannot remove: Operation not permitted  ✅ STICKY BIT WORKS!

exit → exit
lab finish perms-default
```

---

## Special Permissions

### setgid on Directories
```bash
chmod g+s /shared   # or chmod 2xxx
```
New files inherit group of directory automatically.

### Sticky Bit
```bash
chmod +t /shared    # or chmod 1xxx
```
Only file **owner** or root can delete files.

### umask
```bash
umask          # check current
umask 007      # temporary
echo "umask 007" >> ~/.bashrc  # permanent
```

| umask | Files | Dirs |
|-------|-------|------|
| 022 (default) | 644 | 755 |
| 007 | 660 | 770 |

### Combined: chmod 3770
```
3 = setgid(2) + sticky(1)
7 = owner rwx
7 = group rwx
0 = others ---
```

---

## Takeaway
`rm: Operation not permitted` proved sticky bit working in real time. Without it, any group member with `w` on directory can delete anyone's files. With it, only the owner can delete their own.

*Screenshot: [screenshots/RH124/ch11-perms-default-guided.png](../screenshots/RH124/)*
