---
description: MITRE ATT&CK, Persistence, Sub-technique T1136.002
---

# Create Account: Domain Account

After obtaining Domain Administrator access in an engagement I like to create a Domain Administrator account to perform all other post exploitation activities from.&#x20;

Steps from a domain controller to create a domain administrator account:

```powershell
net user parzival password123 /add /domain
net group "Domain Admins" parzival /add /domain
net user parzival /comment:"Account created for authorized pentest. Created on XX/XX/XXXX"
net user parzival /expires:XX/XX/XXXX
```
