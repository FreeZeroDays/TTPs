# Enumeration Checklist

### Windows Checklist

* [ ] Enumerate all TCP ports
  * [ ] Enumerate services and run scripts against these ports: `-sC -sV`
* [ ] Run GoBuster or FeroxBuster against any identified web servers.&#x20;
* [ ] Run SMBMap against any identified SMB services.&#x20;
  * [ ] These can then be manually accessed with SMBClient: `smbclient \\[IP]\[share]`
* [ ] Enumerate LDAP without credentials. Passwords may be stored in cleartext.&#x20;
  * [ ] `ldapsearch -x -h <IP> -D '<DOMAIN>\<username>' -w '<password>' -b "DC=<1_SUBDOMAIN>,DC=<TDL>"`
