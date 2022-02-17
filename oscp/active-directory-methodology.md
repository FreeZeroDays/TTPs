---
description: Notes on OSCP related Active Directory Methodology
---

# Active Directory Methodology

These should be considered 'simple' notes. I tend to overcomplicate things in exams so these are my 'simple' must do's for Active Directory in preparation for the OSCP exam.&#x20;

#### Enumerate all local users:

`net user`

#### Enumerate all users in the domain:&#x20;

`net user /domain`

#### Enumeration Specific Domain User

`net user [USERNAME] /domain`

#### Basic Methodology

1. Gain access to a user on the active directory environment.
2. Enumerate the domain with the commands listed above.
3. Enumerate all computers on the domain.&#x20;
   * Don't just enumerate one computer.. Enumerate them all.
4. Enumerate all users logged onto computers that we have local administrator access to.
5. Kerberoast with any user account acquired (GetUserSPNs, Invoke-Kerberoast, etc)
6. Attempt password spraying against all user accounts
7. Pass the Hash to pivot
   * Also try to Pass the Ticket
8. Run Mimikatz on all systems
   * Enumerate both password hashes and tickets.
