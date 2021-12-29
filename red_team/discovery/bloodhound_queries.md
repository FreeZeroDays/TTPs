# BloodHound Queries

**Description:** BloodHound queries that I use often for domain reconaissance.

### Identify computers with unconstrained delegation enabled:
`MATCH (c:Computer {unconstraineddelegation:true}) RETURN c`

### Identify computers with constrained delegation configured:
`MATCH (c:Computer), (t:Computer), p=((c)-[:AllowedToDelegate]->(t)) RETURN p`
