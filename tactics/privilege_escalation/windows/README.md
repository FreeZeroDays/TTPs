---
description: List of commonly used escalation tools for Windows systems
---

# Windows

### Tools

* [Watson](https://github.com/rasta-mouse/Watson) - Enumerate missing KBs and suggest exploits for Privilege Escalation vulnerabilities
* [Seatbelt](https://github.com/GhostPack/Seatbelt) - Performs a number of security oriented host-survey "safety checks" relevant from both offensive and defensive security perspectives
* [PowerUp](https://github.com/PowerShellMafia/PowerSploit/blob/master/Privesc/PowerUp.ps1) - PowerUp aims to be a clearinghouse of common Windows privilege escalation vectors that rely on misconfigurations
* [Windows-Exploit-Suggester](https://github.com/AonCyberLabs/Windows-Exploit-Suggester) - This tool compares a targets patch levels against the Microsoft vulnerability database in order to detect potential missing patches on the target
* [WinPEAS](https://github.com/carlospolop/PEASS-ng/tree/master/winPEAS) - Windows Privilege Escalation Awesome Scripts
* [BeRoot](https://github.com/AlessandroZ/BeRoot) - Post exploitation tool to check common misconfigurations to find a way to escalate our privilege

### Metasploit

```bash
# When it works you're always happy
getsystem

# Local Exploit Suggester 
post/multi/recon/local_exploit_suggester
```
