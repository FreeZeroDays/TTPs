---
description: MITRE ATT&CK, Credential Access, Sub-technique T1003.005
---

# Cached Domain Credentials

With SYSTEM access, an attacker can dump cached credentials with Mimikatz or Secretsdump. Note that DCC hashes take significantly longer to crack than an NT or Net-NTLM hash. I recommend using a simple password and rule list that has been tailored to your target first.&#x20;

### Cracking

To crack these with Hashcat, the hash needs to be in the following format:

```bash
$DCC2$10240#parzival#e4e938d12fe5974dc42a90120bd9c90f
```

After ensuring the hash is formatted appropriately, they can be cracked with the following command:

```bash
hashcat -m 2100 $dcc_file $wordlist
```

### Mitigations

When researching LSA Secrets on [MITRE](https://attack.mitre.org/techniques/T1003/004/) it appears as though the only mitigation to LSA Secrets being dumped is through detection. However, this is not the case.

The following settings can be configured to remove cached domain credentials from LSA Secrets:

```bash
Cached credential set to 0 on servers
Cached credential set to 1 on workstations
```

### References

{% embed url="https://www.ired.team/offensive-security/credential-access-and-credential-dumping/dumping-and-cracking-mscash-cached-domain-credentials" %}
