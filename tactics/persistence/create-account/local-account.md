---
description: MITRE ATT&CK, Persistence, Sub-technique T1136.001
---

# Local Account

After gaining administrator access to the system run the following command to create a local user account:&#x20;

```powershell
net user parzival password123 /add
```

We then have the option of adding this account to the local administrators group:

```bash
net localgroup administrators parzival /add
```

Finally, we can delete this account once it is no longer needed:

```bash
net user parzival /del
```
