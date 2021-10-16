# Metasploit Datatabase

**Description:** Some tips and tricks around using the Metasploit Framework Dataabse (msfdb) 

## Importing 

* Import Nmap scans into msfdb 

```db_import NmapScan-1000.xml```

* Import scan from Nessus into msfdb

  1. Load the Nessus plugin 

  ```load nessus```

  2. List the completed scans available for import

  ```nessus_scan_list -c```

  Import the specified scan

  ```nessus_db_import [ID]```
