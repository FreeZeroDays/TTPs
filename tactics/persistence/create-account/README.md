---
description: MITRE ATT&CK, Persistence, Technique T1136
---

# Create Account

### Local Account

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

### Domain Account

After obtaining Domain Administrator access in an engagement I like to create a Domain Administrator account to perform all other post exploitation activities from.&#x20;

Steps from a domain controller to create a domain administrator account:

```powershell
net user parzival password123 /add /domain
net group "Domain Admins" parzival /add /domain
net user parzival /comment:"Account created for authorized pentest. Created on XX/XX/XXXX"
net user parzival /expires:XX/XX/XXXX
```
