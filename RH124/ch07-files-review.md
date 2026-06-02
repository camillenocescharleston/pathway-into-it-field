# Ch07 — Managing Files from the Command Line

**Lab:** `files-review` | **Date:** May 10, 2026 | **Result:** ✅ 5/5 PASS

← [Back to RH124](./README.md)

---

## Objectives
- Create and manage files and directories
- Work with hard links and understand inodes
- Manage files on a remote server (`serverb`)
- Verify file permissions and ownership with `ls -l`

---

## Grade: 5/5 ✅

```bash
PASS  Checking files in the chapters directory
PASS  Checking files in the editor directory
PASS  Checking files in the season1 directory
PASS  Checking files in the season2 directory
PASS  Checking that the hard link is correctly created
```

---

## Key Concepts

### Hard Links vs Symbolic Links

| Type | Command | Behavior |
|------|---------|----------|
| Hard link | `ln file link` | Same inode — both entries equal |
| Symbolic link | `ln -s file link` | Pointer — breaks if original deleted |

### Permission String

```
-rw-r--r--.
│└┬┘└┬┘└┬┘└── SELinux context
│ │  │  └── Others: r--
│ │  └───── Group:  r--
│ └──────── Owner:  rw-
└────────── File type
```

---

## Takeaway
Perfect 5/5. Hard link count = 2 means two names for one file, not two copies. Matters in backup systems and forensic file location.

*Screenshot: [screenshots/RH124/ch07-files-review.png](../screenshots/RH124/)*
