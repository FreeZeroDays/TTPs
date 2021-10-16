# Metasploit Datatabase

**Description:** Some tips and tricks around using the Metasploit Framework Dataabse (msfdb) 

## Importing 

* Import Nmap scans into msfdb 

```db_import NmapScan-1000.xml```

* Import Nessus scans into msfdb

  1. Load the Nessus plugin 

    ```load nessus```

  2. List the completed scans available for import

   ```nessus_scan_list -c```

  3. Import the specified scan

   ```nessus_db_import [ID]```
   
## Searching the Database
   
* List all service banners 

```Services -O 6```
   
* List specific port(s)

```services -p 80,443```

* Search for a specific string

```services -S CloudFront```

* Output services that are 'up' to a CSV file 

```services -u -o AliveServices```
