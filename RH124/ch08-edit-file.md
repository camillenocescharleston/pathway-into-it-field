# Ch08 — Editing Files with Vim

**Lab:** `edit-file` | **Date:** May 11, 2026 | **Result:** ✅ PASS

← [Back to RH124](./README.md)

---

## Objectives
- Use `vimtutor` to learn Vim's built-in tutorial
- Create and edit a text file using `vim`
- Practice Normal, Insert, and Command modes
- Verify file contents with `cat`

---

## Commands Used

```bash
[student@servera ~]$ vimtutor       # run twice for practice
[student@servera ~]$ vim filr.txt   # typo: filr instead of file
[student@servera ~]$ cat filr.txt
lab today 5/11/2026
I am really exitide to practice this lab today cause the RH124 is very friendly learner.
I will succeed in this class by lerning hard.
```

---

## Vim Modes

| Mode | Enter With | What You Can Do |
|------|-----------|-----------------|
| Normal | `Esc` | Navigate, delete, yank |
| Insert | `i`, `a`, `o` | Type and edit |
| Command | `:` | Save, quit, search |

## Essential Vim Commands

| Command | Action |
|---------|--------|
| `i` | Insert before cursor |
| `Esc` | Return to Normal |
| `:w` | Save |
| `:q` | Quit |
| `:wq` | Save and quit |
| `:q!` | Quit without saving |
| `dd` | Delete line |
| `u` | Undo |

---

## Takeaway
Typos (`filr.txt`, `exitide`, `lerning`) kept intentionally — they show real learning. Running `vimtutor` twice shows the right instinct. The note written inside: *"I will succeed in this class by lerning hard."* 💪

*Screenshot: [screenshots/RH124/ch08-edit-file.png](../screenshots/RH124/)*
