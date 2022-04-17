---
description: PowerShell remoting for lateral movement
---

# Windows Remote Management

## Enabling PowerShell Remoting

In a PowerShell console running as administrator enable PowerShell Remoting:

```powershell
Enable-PSRemoting –force
```

Set WinRM start mode to automatic:

```powershell
Set-Service WinRM -StartMode Automatic
```

Verify start mode and state:

```powershell
Get-WmiObject -Class win32_service | Where-Object {$_.name -like "WinRM"}
```

## Set Remote Hosts to Trusted

Configure all hosts to be trusted:

```powershell
Set-Item WSMan:localhost\client\trustedhosts -value *
```

Validate trusted hosts configuration:

```powershell
Get-Item WSMan:\localhost\Client\TrustedHosts
```

## Establishing a Session

Interactive session using the current user:

```powershell
Enter-PsSession –ComputerName [HOST]
```

Interactive session with explicit credentials:

```powershell
Enter-PsSession –ComputerName [HOST] –Credentials [DOMAIN\USER]
```

Create a background session using the current user::

```powershell
New-PSSession -ComputerName [HOST]
```

Create a background session with explicit credentials:

```powershell
New-PSSession –ComputerName server1.domain.com –Credentials [DOMAIN\USER]
```

List background sessions:

```powershell
Get-PSSession
```

Interacting with a background session:

```powershell
Enter-PsSession –id [ID]
```

Exiting out of a session:

```powershell
Exit-PsSession
```

Remove all background sessions:

```powershell
Get-PSSession | Disconnect-PSSession
```

## References

* [WinRM for Lateral Movement](https://www.ired.team/offensive-security/lateral-movement/t1028-winrm-for-lateral-movement)
* [PowerShell Remoting Cheatsheet](https://www.netspi.com/blog/technical/network-penetration-testing/powershell-remoting-cheatsheet/)
* [Enable-PSRemoting](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/enable-psremoting?view=powershell-7.1)
* [Enable and Use Remote Commands in Windows PowerShell](https://docs.microsoft.com/en-us/previous-versions/technet-magazine/ff700227\(v=msdn.10\)?redirectedfrom=MSDN)
* [Windows PowerShell - Cool Pipeline Tricks, Redux](https://docs.microsoft.com/en-us/previous-versions/technet-magazine/ff394367\(v=msdn.10\)?redirectedfrom=MSDN)
