---
description: >-
  Privilege escalation using the load and unload device drivers policy
  (SeLoadDriverPrivilege).
---

# Privilege Escalation with SeLoadDriverPrivilege

## Exploitation

Run the following command to see if the privilege is enabled:

```bash
whoami /priv
```

Regardless of if SeLoadDriverPrivilege is enabled or not, we can run the following tool automagically enable the SeLoadDrivierPrivilege, create a registry key under HKEY\_CURRENT\_USER and execute NTLoadDriver.

* [EoPLoadDriver](https://github.com/TarlogicSecurity/EoPLoadDriver/)

Once we have successfully loaded our `Capcom.sys` driver onto the machine we can abuse the malicious driver to escalate our privleges. The following are exploits I've used in my test environment and have verified working:

* [ExploitCapcom](https://github.com/tandasat/ExploitCapcom)
* [PuppetStrings](https://github.com/zerosum0x0/puppetstrings)

This privilege is extremely dangerous to assign to any user and I have seen multiple organizations assign it to _every_ user.

## References

* [Privileged Accounts and Token Privileges](https://www.ired.team/offensive-security-experiments/active-directory-kerberos-abuse/privileged-accounts-and-token-privileges) - Details on this attack from iRed.Team
* [Abusing SeLoadDriverPrivilege for privilege escalation](https://www.tarlogic.com/blog/abusing-seloaddriverprivilege-for-privilege-escalation/) - Detailed walkthrough on attacks from TarLogic
