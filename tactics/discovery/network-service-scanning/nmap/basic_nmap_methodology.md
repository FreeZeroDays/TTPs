---
description: >-
  This details my basic methodology using Nmap for enumeration during a
  penetration test.
---

# Basic Nmap Methodology

## Host Discovery with Nmap

#### Perform a ping sweep with Nmap

```bash
nmap -sn [TARGET]/24 -oA PingSweepHosts
```

#### Custom host discovery with Nmap

```bash
nmap -PS21-25,80,110,139,443,445,623,3306,3389,8000,8080,8081,etc [TARGET]/24 -oA DiscoveredHosts
```

#### Exclude hosts from scans with Nmap by specifying IPs

```bash
nmap -sV -F --exclude 127.0.0.2,127.0.0.4 127.0.0.1/24
```

#### Exclude hosts from scans with Nmap by specifying file

```bash
nmap -sV -F --excludefile [FILENAME] 127.0.0.1
```

#### Create a Live Hosts List

```bash
cat DiscoveredHosts.gnmap | awk '/Up$/{print $2}' > LiveIPs.txt
```

#### Perform a Full Scan on Live Hosts

```bash
nmap -p- -Pn -sV -sC -iL LiveIPs.txt -oA FullScanOutput
```

### Additional scans

#### Custom Discovery Scan

```bash
sudo nmap -Pn -n -sS -p $customports --min-hostgroup 255 --min-rtt-timeout 0ms --max-rtt-timeout 100ms --max-retries 1 --max-scan-delay 0 --min-rate 2000 -oA nmap-discovery -vvv -open -iL $targetfile
```

#### Custom Full Scan

```bash
sudo nmap -Pn -n -p- -sV --min-hostgroup 255 --min-rtt-timeout 25ms --max-rtt-timeout 100ms --max-retries 1 --max-scan-delay 0 --min-rate 1000 -oA full-nmap -vvv --open -iL $targetfile
```

#### Run a vulners scan

```bash
nmap -p- --script=vulners -iL LiveIPs.txt -oA VulnersScan
```

#### Run a default HTTP credential scan

```bash
nmap -p- --script=http-default-accounts -iL LiveIPs.txt -oA DefaultCredentialScan
```

