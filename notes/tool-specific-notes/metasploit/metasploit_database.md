---
description: Some tips and tricks around using the Metasploit Framework Dataabse (msfdb)
---

# Metasploit Datatabase

### Importing

#### Import Nmap scans into msfdb

```bash
db_import NmapScan-1000.xml
```

#### Import Nessus scans into msfdb

Load the Nessus plugin

```bash
load nessus
```

List the completed scans available for import

```bash
nessus_scan_list -c
```

Import the specified scan

```bash
nessus_db_import $id
```

### Searching the Database

#### List all service banners

```bash
services -O 6
```

#### List specific port(s)

```bash
services -p 80,443
```

#### Search for a specific string

```bash
services -S Telnet
```

#### Output services that are 'up' to a CSV file

```bash
services -u -o AliveServices
```
