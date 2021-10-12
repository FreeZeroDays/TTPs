# Validating Scope
* [Hurricane Electric Internet Services](https://bgp.he.net) - Find out who owns an IP Address

# Find Email Addresses
* [Hunter.io](https://hunter.io/) - Identify the email schema used by an organization
* [Phonebook.cz](Phonebook.cz) - Lookup emails related to the organization
* [EmailHippo](https://tools.emailhippo.com) - Validate emails identified are in use by the organization

# External Penetration Testing
* [YAWAST](https://github.com/adamcaudill/yawast) - Amazing for performing initial reconnaissance on a website. Also has a PoC for Sweet32 built into it
* [Skipfish](https://github.com/spinkham/skipfish) - Googles active web application security reconnaissance tool
* [Nuclei](https://github.com/projectdiscovery/nuclei) - Vulnerability scanner that is actively maintained and updated frequently
* [AutoDirBuster](https://github.com/NetSPI/AutoDirbuster) - Parse Nmap scans and run DirBuster against targets. Useful when covering a large scope$
* [FeroxBuster](https://github.com/epi052/feroxbuster) - My replacement for Dirb and other fuzzing tooling

# Password Hunting
* [PwnDB](https://github.com/davidtavarez/pwndb) - Searches for leaked credentials
* [DeHashed](https://dehashed.com/) - Popular way to search for leaked credentials but requires payment
* [Snusbase](https://snusbase.com/) - Alternative to DeHashed
* [Breach-Parse](https://github.com/hmaverickadams/breach-parse) - TCM's script to parse databases and identify leaked credentials
* [pwnedOrNot](https://github.com/thewhiteh4t/pwnedOrNot) - OSINT tool to identify if an account has appeared in a database leak

# Attacking Outlook / Similar Products 
* [Ruler](https://github.com/sensepost/ruler) - A tool to abuse Exchange services
* [O365Spray](https://github.com/0xZDH/o365spray) - My goto when spraying Office 365
* [Msspray](https://github.com/SecurityRiskAdvisors/msspray) - Conduct password attacks against Azure AD and Office 365 endpoints
* [TeamsUserEnum](https://github.com/immunIT/TeamsUserEnum) - User enumeration with the Microsoft Teams API

# LinkedIn Reconnaissance 
* [LeakedInt](https://github.com/vysecurity/LinkedInt) - LinkedIn reconnaissance tool that provides output with picture, name, email, title, and location
* [WeakestLinkl](https://github.com/shellfarmer/WeakestLink) - Reguarly updated LinkedIn recon tool (10/11/2021)
* [LinkedIn2Username](https://github.com/initstring/linkedin2username) - My favorite LinkedIn reconnaissance tool. It should be noted that this tool will not reliably identify all of the emails for a company. 
* [BridgeKeeper](https://github.com/0xZDH/BridgeKeeper/blob/master/core/hunter.py) - LinkedIn reconnaissance tool that works great in combination with LinkedIn2Username
* [EmailGen](https://github.com/navisecdelta/EmailGen) - Email Generation from Bing using LinkedIn Dorks

# Footholds
* [Responder](https://github.com/lgandx/Responder-Windows) - Abuse LLMNR and NBT-NS protocols (and more) to get a reliable foothold
* [mitm6](https://github.com/fox-it/mitm6) - Abuse IPv6 to obtain a foothold
* [Impacket](https://github.com/SecureAuthCorp/impacket) - The options are endless with Impacket. Kerberoast until you drop!
* [Flamingo](https://github.com/atredispartners/flamingo) - Capture credentials sprayed across the network
* [SpoolSploit](https://github.com/BeetleChunks/SpoolSploit) - Collection of Windows print spooler exploits. Great for obtaining a foothold or escalating privileges!

# Credential Spraying and Bruteforce 
* [SprayingToolkit](https://github.com/byt3bl33d3r/SprayingToolkit) - Spraying attacks against Lync/S4B, OWA, and O365
* [CrackMapExec](https://github.com/byt3bl33d3r/CrackMapExec) - Spraying attacks against.. Everything
* [DomainPasswordSpray](https://github.com/dafthack/DomainPasswordSpray) - Spraying attacks against a domain. Gathers account lockout windows which is nifty.
* [Spray](https://github.com/Greenwolf/Spray) - Spraying against Active Directory. 
* [Patator](https://github.com/lanjelot/patator) - Multi-purpose brute-forcer. Takes a little reading of the manual but works incredibly.
* [BruteSpray](https://github.com/x90skysn3k/brutespray) - Brute-Forcing from an Nmap output. One of my favorites for automating the assessment of a network.
