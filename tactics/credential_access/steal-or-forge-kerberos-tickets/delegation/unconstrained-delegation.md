# Unconstrained Delegation

Unconstrained delegation the key distribution center (KDC) places a copy of the users TGT inside the service ticket (TGS). When the TGS is provided to the server for service access, the server opens the TGS and places the user’s TGT into memory for further use. This means that the server can now impersonate the user without any restrictions.&#x20;

### Enumerating Unconstrained Delegation

```bash
# Locate Unconstrained Delegation in BloodHound
MATCH (c:Computer {unconstraineddelegation:true}) RETURN c
```

### Compromising the Domain

After compromising a server with unconstrained delegation enabled, an attacker can extract any and all TGTs from memory to impersonate them against services in the domain. This means that if we identify a Domain Administrators TGT in memory,&#x20;

### Notes

* Domain Controllers always have unconstrained delegation enabled by default.&#x20;
* Using `Rubeus` monitor command is a good way to identify any new TGTs on a compromised server.&#x20;

### References

{% embed url="https://adsecurity.org/?p=1667" %}

{% embed url="https://www.ired.team/offensive-security-experiments/active-directory-kerberos-abuse/domain-compromise-via-unrestricted-kerberos-delegation" %}
