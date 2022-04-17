---
description: BloodHound queries that I use often for domain reconaissance.
---

# BloodHound Queries

### Identify computers with unconstrained delegation enabled:

```bash
MATCH (c:Computer {unconstraineddelegation:true}) RETURN c
```

### Identify computers with constrained delegation configured:

```bash
MATCH (c:Computer), (t:Computer), p=((c)-[:AllowedToDelegate]->(t)) RETURN p
```
