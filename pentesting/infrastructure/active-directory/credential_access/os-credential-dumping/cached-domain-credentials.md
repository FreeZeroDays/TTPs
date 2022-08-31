---
description: MITRE ATT&CK, Credential Access, Sub-technique T1003.005
---

# Cached Domain Credentials

### Description

With SYSTEM access, an attacker can dump cached credentials with Mimikatz or Secretsdump. Note that DCC hashes take significantly longer to crack than an NT or Net-NTLM hash. I recommend using a simple password and rule list that has been tailored to your target first.&#x20;

### Cracking

To crack these with Hashcat, the hash needs to be in the following format:

```bash
$DCC2$10240#tom#e4e938d12fe5974dc42a90120bd9c90f
```

After ensuring the hash is formatted appropriately, they can be cracked with the following command:

```bash
hashcat -m 2100 $dcc_file $wordlist
```

### References

{% embed url="https://hashcat.net/wiki/doku.php?id=example_hashes" %}
