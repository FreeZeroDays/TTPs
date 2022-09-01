---
description: Just a few quick Hashcat tips that may come in useful.
---

# Hashcat Tips

## Password Cracking Tips

* Loopback will take all of the discovered passwords from cracking and apply the rules specified when beginning the attack against them. Simply append `--loopback` to your Hashcat command.
* If you are experiencing the error `CL_OUT_OF_RESOURCES` on Windows 10 when running Hashcat, then you can add the following to the registry to remove it: `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\GraphicsDrivers` then add "TdrLevel" as a DWORD with value 0.&#x20;
