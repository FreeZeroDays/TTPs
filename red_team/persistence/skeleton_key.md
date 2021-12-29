# Skeleton Key

**Description:** Persistence utilizing a skeleton key attack. 

### Creating the Skeleton Key
`mimikatz !misc::skeleton`

This will allow you (by default) to log in with any domain administraotrs account using the password `mimikatz`


**Notes:** This should not be used unless requested by a client. A skeleton key cannot be removed until the domain controllers are restarted and it is possible for this attack to cause unintended effects.
