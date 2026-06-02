# Ch09 — Shell I/O Redirection

**Lab:** `shellio-redirect` | **Date:** May 11, 2026 | **Result:** ✅ PASS

← [Back to RH124](./README.md)

---

## Objectives
- Use `>` and `>>` to redirect stdout
- Use `2>` to redirect stderr
- Use `tee` and `tee -a`
- Use `wc -l` and `find`

---

## Commands Used

```bash
echo "Log file with errors: 20250507.log" > ~/finding.txt
find /etc -name '*.conf' > results.txt 2> search_error.txt
wc -l results.txt | tee a findings.txt
wc -l search_error.txt | tee a finding.txt
19 search_error.txt
date >> finding.txt
cat finding.txt
```

## Typo Spiral (real session)
```bash
wc -l serach_errors.txt   # typo 1
wc -l search_errors.txt   # typo 2  
wc -l search_error.txt    # correct ✅
```
**Lesson:** Always `ls` first to verify exact filename.

---

## I/O Redirection Cheat Sheet

| Operator | Meaning |
|----------|---------|
| `>` | Redirect stdout — **overwrites** |
| `>>` | Redirect stdout — **appends** |
| `2>` | Redirect stderr |
| `&>` | Both stdout and stderr |
| `\|` | Pipe to next command |
| `tee` | Write to stdout AND file |
| `tee -a` | Write to stdout AND append |

---

*Screenshot: [screenshots/RH124/ch09-shellio-redirect.png](../screenshots/RH124/)*
