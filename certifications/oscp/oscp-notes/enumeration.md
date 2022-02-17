---
description: Rough notes on enumeration
---

# Enumeration

* Ensure you run FeroxBuster or GoBuster with file extensions identified throughout inital enumeration of the device.
* Personally I like running the following scans to perform enumeration:
  1. `nmap -sV -sC -p- --min-rate 1000 -T4 [IP] -oA Full-TCP-Scan`
  2. `nmap -sU --top-ports 1000 -T4 [IP] -oA Quick-UDP-Scan`
  3. `nmap -p[PORTS] --script=vuln [IP] -oA Vuln-Scan`
* If Ident is available then we may be able to enumerate users. While `nmap -sC` should successfully enumerate users as well, it is good to double check.&#x20;
  * Install ident-user-enum: `apt install ident-user-enum`
  * Run it against all identified ports: `ident-user-enum [IP] 22 53 113 5432 8080 1000`Iden
