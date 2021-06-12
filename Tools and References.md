# External / Basic Web App
* Yawast - https://github.com/adamcaudill/yawast
* Skipfish - https://github.com/spinkham/skipfish
* Nuclei - https://github.com/projectdiscovery/nuclei

# Footholds
* Responder - https://github.com/lgandx/Responder-Windows
* MITM6 - https://github.com/fox-it/mitm6
* CrackMapExec - https://github.com/byt3bl33d3r/CrackMapExec
* DomainPasswordSpray (PS1) - https://github.com/dafthack/DomainPasswordSpray
* Impacket - https://github.com/SecureAuthCorp/impacket

# Databases 
* DBeaver (Awesome DB tool) - https://dbeaver.io/

# SSL/TLS Configuration
* testssl (Comprehensive tests) - https://github.com/drwetter/testssl.sh
* SSLScan - https://github.com/rbsec/sslscan

# Enumeration
* RustScan - https://github.com/RustScan/RustScan
* ElasticSearch NSE Script - https://github.com/theMiddleBlue/nmap-elasticsearch-nse
* Enum4Linux - https://github.com/CiscoCXSecurity/enum4linux
     Grep out users and admins if enum4linux works:
  ```$cat dcenum.txt | grep “Domain Users” | awk {‘print $8′} | cut -d \\ -f 2 > users.txt```
  ```$cat dcenum.txt | grep “Domain Admins” | awk {‘print $8′} | cut -d \\ -f 2 > admins.txt``` 

# Passive 
* BruteShark - https://github.com/odedshimon/BruteShark
* NetworkMiner (Usually more l00t than BruteShark but costs $$$) - https://www.netresec.com/
* PCredz - https://github.com/lgandx/PCredz

# Post Exploitation
* Nishang - https://github.com/samratashok/nishang
* PowerSploit - https://github.com/PowerShellMafia/PowerSploit
* BetterSafetyKatz - https://github.com/Flangvik/BetterSafetyKatz
* ldapdomaindump - https://github.com/dirkjanm/ldapdomaindump

# Cracking 
* PACK (Awesome password cracking goodies) - https://github.com/iphelix/pack 
* Hate_Crack - https://github.com/trustedsec/hate_crack
* HAT - https://github.com/sp00ks-git/hat

# Wireless
* WiFite 2 - https://github.com/derv82/wifite2

# Obfuscation
* darkarmour - https://github.com/bats3c/darkarmour
* PEzor - https://github.com/phra/PEzor

# Unix
* Bashark (Post exploitation toolkit in a bash script) - https://github.com/redcode-labs/Bashark/blob/master/bashark.sh
* Mimipenguin (mimikatz for unix) - https://github.com/huntergregal/mimipenguin

# Misc
* PwnCat - https://github.com/calebstewart/pwncat
* UpDog -https://github.com/sc0tfree/updog
* SIET - https://github.com/Sab0tag3d/SIET
* OffensivePipeline (Make tools quicker in Powershell) - https://github.com/Aetsu/OffensivePipeline

# Sites I Reference All The Time
* HackTricks - https://book.hacktricks.xyz/
* Post Exploitation Windows Commands - https://int0x33.medium.com/day-26-the-complete-list-of-windows-post-exploitation-commands-no-powershell-999b5433b61e
* WADComs - https://wadcoms.github.io/
* iRedTeam - https://www.ired.team/
* Tips for Pentesting a PCI Environment (Good sanity checks) - https://secureideas.com/blog/2018/08/tips-for-penetration-testing-a-pci-environment.html
* Dumping and Cracking mscash - https://www.ired.team/offensive-security/credential-access-and-credential-dumping/dumping-and-cracking-mscash-cached-domain-credentials
