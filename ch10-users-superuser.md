# Ch10 — Gain Superuser Access

**Lab:** `users-superuser` | **Date:** May 30, 2026 | **Result:** ✅ PASS
**Time:** 20:11 → 20:25 | **Lab URL:** `rol.redhat.com/rol/app/courses/rh124-10.0/pages/ch10s04`

← [Back to RH124](./README.md)

---

## Objectives
- Use `sudo` to switch to root without knowing root password
- Verify `su` command behavior
- Read a restricted system log with `sudo`
- Understand sudoers and principle of least privilege

---

## Commands Used

```bash
student@workstation:~$ lab start users-superuser
SUCCESS  Check connections - servera, serverb
SUCCESS  Ensuring required packages installed
SUCCESS  Ensuring operator1 user added
SUCCESS  Configure operator1 as sudoer
SUCCESS  Ensuring operator1 password added

student@workstation:~$ ssh servera
[student@servera ~]$ sudo -i
[root@servera ~]# sudo tail -5 /var/log/messages
May 30 20:23:42 servera NetworkManager[1049]: device(ens4): disconnected -> prepare -> config -> ip-config -> DHCP

[root@servera ~]# exit
[student@servera ~]$ exit
Connection to servera closed.

student@workstation:~$ lab finish users-superuser
SUCCESS  Removing the sudoers file for operator1
SUCCESS  Removing operator1 user
```

---

## sudo vs su

| Command | Requires | Use Case |
|---------|----------|----------|
| `sudo -i` | Your password | Full root session |
| `sudo cmd` | Your password | One-off admin task |
| `su -` | Root password | Old-school root switch |
| `su - user` | Target password | Switch user + environment |

---

## Takeaway
As a Security Officer, I apply least privilege daily. `sudo` is that same principle in Linux — every elevated command is logged with the user's identity in `/var/log/secure`. That audit trail is what SOC analysts use to reconstruct exactly who did what and when.

*Screenshot: [screenshots/RH124/ch10-users-superuser.png](../screenshots/RH124/)*
