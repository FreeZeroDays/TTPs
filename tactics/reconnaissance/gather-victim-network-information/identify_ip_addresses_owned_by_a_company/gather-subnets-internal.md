# Gather Subnets - Internal

Recently I came across a CrackMapExec module that would have come in useful on closed door penetration tests. This allows us to extract subnet information from Active Directory assuming that we have the following:

* Valid credentials for the domain
* Can query LDAP

We can then use CrackMapExec's `subnets` module against the domain controller:

```bash
crackmapexec ldap $ip -d $domain -u $username -p $password -M subnets
```

### References

{% embed url="https://podalirius.net/en/articles/active-directory-sites-and-subnets-enumeration/" %}
