# Validating Scope
* [Hurricane Electric Internet Services](https://bgp.he.net) - Find out who owns an IP Address

# Find Email Addresses
* [Hunter.io](https://hunter.io/) - Identify the email schema used by an organization
* [Phonebook.cz](Phonebook.cz) - Lookup emails related to the organization
* [EmailHippo](https://tools.emailhippo.com) - Validate emails identified are in use by the organization

# Phishing
* [GoPhish](https://github.com/gophish/gophish) - An incredible open-source phishing framework
* [Evilginx2](https://github.com/kgretzky/evilginx2) - Man-in-the-middle attack framework for phishing login credentials and bypassing 2fa
* [Catphish](https://github.com/ring0lab/catphish) - Generate similar looking domains for use in phishing attacks
* [Boobsnail](https://github.com/STMSolutions/boobsnail) - Generate malicious XLM documents for phishing
* [MacroPack](https://github.com/sevagas/macro_pack) - Automize obfuscation of Office documents

# External Penetration Testing
* [YAWAST](https://github.com/adamcaudill/yawast) - Amazing for performing initial reconnaissance on a website. Also has a PoC for Sweet32 built into it
* [Skipfish](https://github.com/spinkham/skipfish) - Googles active web application security reconnaissance tool
* [Nuclei](https://github.com/projectdiscovery/nuclei) - Vulnerability scanner that is actively maintained and updated frequently
* [AutoDirBuster](https://github.com/NetSPI/AutoDirbuster) - Parse Nmap scans and run DirBuster against targets. Useful when covering a large scope$
* [FeroxBuster](https://github.com/epi052/feroxbuster) - My replacement for Dirb and other fuzzing tooling
* [Amass](https://github.com/OWASP/Amass) - In-depth attack surface mapping. Great for asset discovery and performing external reconnaissance
* [Dorkbot] - Scan Google search results for vulnerabilities with dorks

# Password Hunting
* [PwnDB](https://github.com/davidtavarez/pwndb) - Searches for leaked credentials
* [DeHashed](https://dehashed.com/) - Popular way to search for leaked credentials but requires payment
* [Snusbase](https://snusbase.com/) - Alternative to DeHashed
* [Breach-Parse](https://github.com/hmaverickadams/breach-parse) - TCM's script to parse databases and identify leaked credentials
* [pwnedOrNot](https://github.com/thewhiteh4t/pwnedOrNot) - OSINT tool to identify if an account has appeared in a database leak

# Scanning/Enumeration Tools
* [RustScan](https://github.com/RustScan/RustScan) - Alternative to Nmap. Port scanning goes brrr
* [Nmap-Elasticsearch-NSE](https://github.com/theMiddleBlue/nmap-elasticsearch-nse) - NSE script for scanning Elasticsearch. Useful when identified in a penetration test.
* [Enum4Linux](https://github.com/CiscoCXSecurity/enum4linux) - Useful for gathering information from a host with anoymous access or authenticating to a DC to obtain a list of usernames
* [Autorecon](https://github.com/Tib3rius/AutoRecon) - Automated enumeration of services
* [Aquatone](https://github.com/michenriksen/aquatone) - Visually inspect websites. Has the ability to parse Nmap scans
* [EyeWitness](https://github.com/FortyNorthSecurity/EyeWitness) - Visually inspect websites. My preferred tool of choice. Has the ability to parse Nessus scans

# LinkedIn Reconnaissance 
* [LeakedInt](https://github.com/vysecurity/LinkedInt) - LinkedIn reconnaissance tool that provides output with picture, name, email, title, and location
* [WeakestLink](https://github.com/shellfarmer/WeakestLink) - Reguarly updated LinkedIn recon tool (10/11/2021)
* [LinkedIn2Username](https://github.com/initstring/linkedin2username) - My favorite LinkedIn reconnaissance tool. It should be noted that this tool will not reliably identify all of the emails for a company. 
* [BridgeKeeper](https://github.com/0xZDH/BridgeKeeper/blob/master/core/hunter.py) - LinkedIn reconnaissance tool that works great in combination with LinkedIn2Username
* [EmailGen](https://github.com/navisecdelta/EmailGen) - Email Generation from Bing using LinkedIn Dorks

# Passive Reconnaissance 
* [BruteShark](https://github.com/odedshimon/BruteShark) - Analyze PCAPs. Can extract useful data and create a network diagram
* [NetworkMiner](https://www.netresec.com/) - Analyze PCAPs. The free version is great but the professional is better (costs $$$)
* [PCredz](https://github.com/lgandx/PCredz) - My favorite way to analyze PCAPs or live captures. Free, fast, and great for PCI tests

# Footholds
* [Responder](https://github.com/lgandx/Responder-Windows) - Abuse LLMNR and NBT-NS protocols (and more) to get a reliable foothold
* [mitm6](https://github.com/fox-it/mitm6) - Abuse IPv6 to obtain a foothold
* [Impacket](https://github.com/SecureAuthCorp/impacket) - The options are endless with Impacket. Kerberoast until you drop!
* [Flamingo](https://github.com/atredispartners/flamingo) - Capture credentials sprayed across the network
* [SpoolSploit](https://github.com/BeetleChunks/SpoolSploit) - Collection of Windows print spooler exploits. Great for obtaining a foothold or escalating privileges!
* [RouterSploit](https://github.com/threat9/routersploit) - Router exploitation framework
* [SIET](https://github.com/Sab0tag3d/SIET) - Smart Install Exploitation Tool

# Credential Spraying and Bruteforce 
* [SprayingToolkit](https://github.com/byt3bl33d3r/SprayingToolkit) - Spraying attacks against Lync/S4B, OWA, and O365
* [CrackMapExec](https://github.com/byt3bl33d3r/CrackMapExec) - Spraying attacks against.. Everything
* [DomainPasswordSpray](https://github.com/dafthack/DomainPasswordSpray) - Spraying attacks against a domain. Gathers account lockout windows which is nifty
* [Spray](https://github.com/Greenwolf/Spray) - Spraying against Active Directory
* [Patator](https://github.com/lanjelot/patator) - Multi-purpose brute-forcer. Takes a little reading of the manual but works incredibly
* [BruteSpray](https://github.com/x90skysn3k/brutespray) - Brute-Forcing from an Nmap output. One of my favorites for automating the assessment of a network

# Default Credentials
* [nndefaccts](https://github.com/nnposter/nndefaccts) - Updated Nmap default credential list
* [ChangeMe](https://github.com/ztgrace/changeme) - Default credential scanner. I've had mixed results with this. When it works it's great!
* [DefaultCredsCheatsheet](https://github.com/ihebski/DefaultCreds-cheat-sheet) - List of common default credentials
* [HAT](https://github.com/sp00ks-git/hat) - Hashcat Automation Tool

# Wordlists
* [OneRuleToRuleThemAll](https://github.com/NotSoSecure/password_cracking_rules) - My favorite rule list
* [ProbableWordlists](https://github.com/berzerk0/Probable-Wordlists) - Probable wordlists to use in password attacks

# Password Cracking
* [Hashcat](https://github.com/hashcat/hashcat) - This should go without saying.. But Hashcat is amazing
* [PACK](https://github.com/iphelix/pack ) - Password Analysis and Cracking Toolkit. There's a lot of password goodies and resources here
* [Hate_Crack](https://github.com/trustedsec/hate_crack) - TrustedSec's password cracking utility. Automates a lot
* [Pipal](https://github.com/digininja/pipal) - Perform password analysis 

# Database
* [DBeaver](https://dbeaver.io/) - One of the best tools I've used to interact with databases.

# Command and Control
* [Covenant](https://github.com/cobbr/Covenant) - I used Covenant throughout the CRTO certification and fell in love. Free and easy to use
* [Sliver](https://github.com/BishopFox/sliver) - Bishop Fox's C2 framework
* [Shad0w](https://github.com/bats3c/shad0w) - Bats3c's C2. Used it a few times and it's a ton of fun!
* [Mythic](https://github.com/its-a-feature/Mythic) - Cross-platform C2. Previously used while on an OSX engagement

# Amazon Web Services (AWS)
* [Pacu](https://github.com/RhinoSecurityLabs/pacu) - AWS exploitation fraemwork from RhinoSecurityLabs
* [Scour](https://github.com/grines/scour) - AWS red teaming framework

# Attacking Outlook / Similar Products 
* [Ruler](https://github.com/sensepost/ruler) - A tool to abuse Exchange services
* [O365Spray](https://github.com/0xZDH/o365spray) - My goto when spraying Office 365
* [Msspray](https://github.com/SecurityRiskAdvisors/msspray) - Conduct password attacks against Azure AD and Office 365 endpoints
* [TeamsUserEnum](https://github.com/immunIT/TeamsUserEnum) - User enumeration with the Microsoft Teams API

# Obfuscation
* [Darkarmour](https://github.com/bats3c/darkarmour) - Bats3c's obfuscation tool. 
* [PEzor](https://github.com/phra/PEzor) - Shellcode and PE packer
* [PowerShellArmoury](https://github.com/cfalta/PowerShellArmoury) - Store obfuscated pentesting tools in one place
* [Invoke-Obfuscation](https://github.com/danielbohannon/Invoke-Obfuscation) - PowerShell script obfuscator
* [Chameleon](https://github.com/klezVirus/chameleon) - PowerShell obfuscator. I've had a lot of success using this tool
* [Powerglot](https://github.com/mindcrypt/powerglot) - Powershell obfuscator using polyglots

# Unix
* [Bashark](https://github.com/redcode-labs/Bashark/blob/master/bashark.sh) - Post exploitation toolkit in a bash script
* [Mimipenguin](https://github.com/huntergregal/mimipenguin) - Mimikatz for Unix
* [Emp3r0r](https://github.com/jm33-m0/emp3r0r) - A customizable post exploitation Linux framework

# MacOS
* [Mystikal](https://github.com/D00MFist/Mystikal) - Payload generator for MacOS
* [MacOSRedTeaming](https://github.com/tonghuaroot/Awesome-macOS-Red-Teaming) - Mac red teaming resources

# Wireless Attacks
* [WiFite2](https://github.com/derv82/wifite2) - Automate attack against WiFi

# SSL/TLS Auditing
* [TestSSL](https://github.com/drwetter/testssl.sh) - One of the more comprehensive SSL/TLS testing tools I've used
* [SSLScan](https://github.com/rbsec/sslscan) - Useful when SSLyze doesn't work as intended
* [SSLyze](https://github.com/nabla-c0d3/sslyze) - Useful when SSLScan doesn't work as intended

# SSH Auditing
* [SSH-Audit](https://github.com/jtesta/ssh-audit) - Comprehensive audit of SSH. Provides comprehensive information about the SSH server in use

# SMTP
* [Swaks](https://github.com/jetmore/swaks) - Swiss army knife for SMTP testing

# Post Exploitation
* [Nisahng](https://github.com/samratashok/nishang) - Collection of offensive PowerShell scripts for use in penetration testing and red teaming
* [PowerSploit](https://github.com/PowerShellMafia/PowerSploit) - Collection of offensive PowerShell scripts, useful in all phases of testing
* [BetterSafetyKatz](https://github.com/Flangvik/BetterSafetyKatz) - Runs Mimikatz but better
* [LdapDomainDump](https://github.com/dirkjanm/ldapdomaindump) - Dump information about the domain. Incredibly useful for escalating privileges or gathering additional information for spraying attacks
* [Conf-Thief](https://github.com/antman1p/Conf-Thief) - Exfiltrate sensitive data from Confluence
* [BloodHound](https://github.com/BloodHoundAD/BloodHound) - Need I say more? Find attack paths and own the domain
* [Snaffler](https://github.com/SnaffCon/Snaffler) - Find delicious candy on a domain 
* [Pwncat](https://github.com/calebstewart/pwncat) - Netcat on steroids. Post exploitation tool that has some neat tools built into it
* [KeeFarce](https://github.com/denandz/KeeFarce) - Extract passwords from a KeePass 2.x database from memory
* [PingCastle](https://www.pingcastle.com) - Grab information about Active Directory (this tool does way more, check it out)
* [ADRecon](https://github.com/adrecon/ADRecon) - Gathers information about Active Directory

# Penetration Testing Reports
* [PublicPentestingResources](https://github.com/juliocesarfort/public-pentesting-reports) - Repository of public pentesting resources

# Hardening
* [SecureKali](https://github.com/gh0x0st/Secure_Kali) - Tips to secure Kali Linux installation

# Miscellanious
* [OffensivePipeline](https://github.com/Aetsu/OffensivePipeline) - Build tools within PowerShell
* [Depix](https://github.com/beurtschipper/Depix) - Recover information from pixelized screenshots
