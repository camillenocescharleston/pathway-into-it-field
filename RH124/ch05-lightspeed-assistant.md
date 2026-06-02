# Ch05 — Red Hat Lightspeed Assistant

**Lab:** `lightspeed-assistant` | **Date:** May 9, 2026 | **Result:** ✅ PASS

← [Back to RH124](./README.md)

---

## Objectives
- Interact with Red Hat Lightspeed AI assistant integrated into RHEL
- Use AI-assisted administration on a managed server
- Practice RHSM configuration and cleanup

---

## Commands Used

```bash
[student@servera ~]$ exit
Logout
Connection to servera closed.
```

```bash
# Typo caught by system
student@workstation:~$ lab finish ligthspeed-assistant
Lab script name typo detected! Did you mean: lab finish lightspeed-assistant
```

```bash
student@workstation:~$ lab finish lightspeed-assistant
Running: lab finish lightspeed-assistant
SUCCESS  Removing httpd on servera
SUCCESS  Removing CLA on servera
SUCCESS  Unregistering servera from RHSM
SUCCESS  Reversing RHSM configuration on servera
```

---

## Key Concepts

| Concept | Explanation |
|---------|-------------|
| Red Hat Lightspeed | AI assistant built into RHEL |
| CLA | Command Line Assistant |
| `httpd` | Apache HTTP Server |
| RHSM | Red Hat Subscription Manager |

---

## Takeaway
The typo detection by the `lab` command: production servers don't give you helpful suggestions — they fail. Slow down and verify command names before pressing Enter.

*Screenshot: [screenshots/RH124/ch05-lightspeed-assistant.png](../screenshots/RH124/)*
