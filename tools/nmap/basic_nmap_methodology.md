# Basic Nmap Methodology 

This details my basic methodology using Nmap for enumeration during a penetration test.

# Host Discovery with Nmap

Perform a ping sweep with Nmap 

```nmap -sn [TARGET]/24 -oA PingSweepHosts```

Custom host discovery with Nmap 

```nmap -PS21-25,80,110,139,443,445,623,3306,3389,8000,8080,8081,etc [TARGET]/24 -oA DiscoveredHosts```

Exclude hosts from scans with Nmap by specifying IPs

```nmap -sV -F --exclude 127.0.0.2,127.0.0.4 127.0.0.1/24```

Exclude hosts from scans with Nmap by specifying file

```nmap -sV -F --excludefile [FILENAME] 127.0.0.1```

# Create a Live Hosts List 

```cat DiscoveredHosts.gnmap | awk '/Up$/{print $2}' > LiveIPs.txt```

# Perform a Full Scan on Live Hosts 

```nmap -p- -Pn -sV -sC -iL LiveIPs.txt -oA FullScanOutput```

# Additional scans 

Run a vulners scan \
```nmap -p- --script=vulners -iL LiveIPs.txt -oA VulnersScan```

Run a scan for default credentials \
```nmap -p- --script=http-default-accounts -iL LiveIPs.txt -oA DefaultCredentialScan```
