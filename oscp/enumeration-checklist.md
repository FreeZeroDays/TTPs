---
description: >-
  Compilation of checklists I've crafted that were edited when learning new
  techniques throughout various CTFs.
---

# Enumeration Checklist

### General Checklist

* [ ] Perform an nslookup.
  * `nslookup [IP]`
* [ ] Perform a zone transfer.
  * `dig axfr @[IP]`
* [ ] Run enum4linux against the host.&#x20;
  * Ensure you upgrade to the latest version of enum4linux as the one shipped on Kali appears to be broken as of writing this.
  * Alternatively, use [enum4linux-ng](https://github.com/cddmp/enum4linux-ng)

### Web Server Checklist

* [ ] Read entire pages to enumerate any potential usernames and/or emails.
* [ ] Check for `/robots.txt`
* [ ] Check SSL certificates for any usernames
* [ ] Run GoBuster or FeroxBuster against any identified web servers.&#x20;
  * Ensure that any identified extensions are also specified.&#x20;
    * `feroxbuster -u [IP] -x php,html`
    * Check all directories identified for hidden information.
* [ ] Enumerate any available applications to identify version numbers.
  * CMS, Server installation pages, Wappalyzer
* [ ] View source code.
  * Hidden developer comments
  * Usernames/passwords
  * Hidden pages
* [ ] Test any identified parameters for LFI, RFI, SQLi, etc.&#x20;
* [ ] Run Nikto
* [ ] Test all login pages for default passwords
  * admin/admin
  * Google default passwords for the identified application.
* [ ] Attempt to bypass a login page with simple SQLi
* [ ] Register an account and test any additionally identified parameters or forms.
* [ ] Scan for Heartbleed
  * `sslscan [IP]`

### Windows Checklist

* [ ] Enumerate all TCP ports
  * Enumerate services and run scripts against these ports: `-sC -sV`
* [ ] Run SMBMap against any identified SMB services.&#x20;
  * These can then be manually accessed with SMBClient: `smbclient \\[IP]\[share]`
  * Make sure you revisit SMB shares if credentials are identified.
* [ ] Enumerate RPC with rpcclient.
  * `rpcclient -U '' [IP]`
    * Enumerate all users with: `enumdomusers`
    * Enumerate information about a specific user: `queryuser parzival`
    * Enumerate all groups on the system: `querydomgroups`
    * Enumerate descriptions and other important information: `querydispinfo`
    * Resolute is a great video on enumeration with rpcclient if additional information is needed.
* [ ] Enumerate LDAP without credentials. Passwords may be stored in cleartext.&#x20;
  * `ldapsearch -x -h <IP> -D '<DOMAIN>\<username>' -w '<password>' -b "DC=<1_SUBDOMAIN>,DC=<TDL>"`
* [ ] If WebDAV is identified throughout enumeration we can upload a shell using `Cadver`
  * If authenticated to WebDAV then we can use `davtest` to test file extensions and upload a reverse shell.&#x20;
    * `davtest -auth [USER]:[PASSWORD] -sendbd auto -url http://[IP'`

### Windows Privilege Escalation Resources

* [Sushant's Privilege Escalation Guide](https://sushant747.gitbooks.io/total-oscp-guide/content/privilege\_escalation\_windows.html)
* [Absoloom's Guide](https://www.absolomb.com/2018-01-26-Windows-Privilege-Escalation-Guide/)
* [Fuzzy Security Guide](https://www.fuzzysecurity.com/tutorials/16.html)
* [HackTricks Checklist](https://book.hacktricks.xyz/windows/checklist-windows-privilege-escalation)
* [Privilege Escalation Guide (one of the best)](https://infosecwriteups.com/privilege-escalation-in-windows-380bee3a2842)
