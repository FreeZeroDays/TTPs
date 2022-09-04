---
description: BloodHound queries that I use often for domain reconaissance.
---

# BloodHound

BloodHound is an Active Directory reconaisssance tool that can reveal a significant amount of information such as hidden relationships, trusts, and attack paths.&#x20;

### Queries

#### Identify Users with an SPN Set

```bash
MATCH (u:User {hasspn:true}) RETURN u
```

#### Identify computers with unconstrained delegation enabled:

```bash
MATCH (c:Computer {unconstraineddelegation:true}) RETURN c
```

#### Identify computers with constrained delegation configured:

```bash
MATCH (c:Computer), (t:Computer), p=((c)-[:AllowedToDelegate]->(t)) RETURN p
```

#### Identify computers with LAPS enabled:

```bash
MATCH (c:Computer {haslaps: true}) RETURN c
```

### References

{% embed url="https://github.com/BloodHoundAD/BloodHound" %}

{% embed url="https://github.com/fox-it/BloodHound.py" %}
