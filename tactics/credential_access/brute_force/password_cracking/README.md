---
description: MITRE ATT&CK, Credential Access, Sub-technique T1110.002
---

# Password Cracking

### Common Cracking Modes

* `1000` - Crack NTLM hash.&#x20;
* `1100` - Crack DCC hash.&#x20;
* `5500` - Crack Net-NTLMv1&#x20;
* `5600` - Crack Net-NTLMv2
* `13100` - Crack Kerberoasted hash.&#x20;
* `27100` - Crack Net-NTLMv2 to an NTLM hash.&#x20;

### Create a Custom Wordlist for Cracking

1\. Create a simple wordlist or use `cewl` to generate one:

```
Acme (Domain)
Autumn
Winter
Spring
Summer
Welcome
```

2\. Utilize hashcat to run rules on the previous wordlist:

```bash
hashcat $wordlist -r /usr/share/hashcat/rules/best64.rule --stdout > newwordlist
```

### Password Cracking Tips

* Loopback will take all of the discovered passwords from cracking and apply the rules specified when beginning the attack against them. Simply append `--loopback` to your Hashcat command.
* If you are experiencing the error `CL_OUT_OF_RESOURCES` on Windows 10 when running Hashcat, then you can add the following to the registry to remove it: `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\GraphicsDrivers` then add "TdrLevel" as a DWORD with value 0.&#x20;
* A longer password list != better.&#x20;

### Wordlists

* [SecLists](https://github.com/danielmiessler/SecLists)
* [Probable-Wordlists](https://github.com/berzerk0/Probable-Wordlists)
* [PasswordList](https://github.com/Cyb3r4rch3r/PasswordList)
* [WeakPass](https://weakpass.com/wordlist)
* [WeakPasswords](http://weakpasswords.net)
* [Kaonashi](https://github.com/kaonashi-passwords/Kaonashi)

### Hashcat Rulesets

* [OneRuleToRuleThemAll](https://github.com/NotSoSecure/password\_cracking\_rules)
* [NSA-Rules](https://github.com/NSAKEY/nsa-rules)
* [Pantagrule](https://github.com/rarecoil/pantagrule)
* [InsidePro-PasswordsPro](https://github.com/hashcat/hashcat/blob/master/rules/InsidePro-PasswordsPro.rule)
* [Hob0Rules](https://github.com/praetorian-inc/Hob0Rules)
