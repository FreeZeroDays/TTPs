---
description: Some tips and tricks around using the Metasploit Framework Dataabse (msfdb)
---

# Metasploit Datatabase

### Importing Scans

```bash
# Importing an Nmap scan into msfdb
db_import NmapScan-1000.xml

# Importing a Nessus scan into msfdb
load nessus
nessus_scan_list -c
nessus_db_import $id
```

### Searching the Database

```bash
# List all service banners
services -O 6

# List specific port(s)
services -p 80,443

# Search for a specific string
services -S telnet

# Output services that are 'up' to a CSV file
services -u -o AliveServices
```
