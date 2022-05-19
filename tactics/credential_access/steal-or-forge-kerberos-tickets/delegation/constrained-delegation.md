# Constrained Delegation

### Description

Constrained delegation is a safer way to perform Kerberos delegation. In contrast to unconstrained delegation, constrained delegation restricts the services to which the server an act on behalf of a user. This means that the server can be configured to only present delegated credentials to the database server, instead of any other arbitrary service.

### Enumerating Constrained Delegation

```bash
# Enumerating with PowerView
Get-DomainComputer -TrustedToAuth -Properties DnsHostName, MSDS-AllowedToDelegateTo

# Enumerating with BloodHound
MATCH (c:Computer), (t:Computer), p=((c)-[:AllowedToDelegate]->(t)) RETURN p
```

### Notes

* When enumerating constrained delegation, enumerating the service type is extremely important. For exampke, enumerating `cifs` means that we are able to execute PsExec against the host as well as upload and/or download files.&#x20;

### References

{% embed url="https://sensepost.com/blog/2022/constrained-delegation-considerations-for-lateral-movement/" %}

{% embed url="http://blog.redxorblue.com/2019/12/no-shells-required-using-impacket-to.html" %}

{% embed url="https://posts.specterops.io/hunting-in-active-directory-unconstrained-delegation-forests-trusts-71f2b33688e1" %}
