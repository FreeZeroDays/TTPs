---
description: MITRE ATT&CK, Defense Evasion, Sub-technique T1562.002
---

# Disable Windows Event Logging

### Description

Disabling Windows event logging allows for an attacker to operate on a compromised host while leaving minimal evidence behind.&#x20;

### Methods

#### Disable the EventLog service with PowerShell:

```powershell
Stop-Service -Name EventLog
```

#### Disable auditing for the Account Logon Category:

```powershell
auditpol /set /category:"Account Logon" /success:disable /failure:disable
```

#### Clear the Audit Policy

```powershell
auditpol /clear /y
auditpol /remove /allusers
```

### References

{% embed url="https://attack.mitre.org/techniques/T1562/002/" %}
