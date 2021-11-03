# Segmentation Testing Notes

**Description:** When performing segmentation tests for PCI compliance, there aside from my Nmap scans there are a few things I've wanted to keep jotted down. This section contains my notes.

## Basic Checks 

Below are some basic commands to use when performing a segmentation test. These should be modified in order to be more thorough. 

### ICMP 
```nmap -sn 10.0.0.0/24 -oA ICMP_Check```

### TCP 
```nmap -sS -Pn -p- -oA TCP_Check```

### UDP 
```nmap -sU -Pn --top-ports 1000 -oA UDP_Check```

### IPv6
```nmap -6 [IPv6_Address] -oA IPv6_Scan```

## Notes

* When performing a segmentation test against FortiGate devices, port 113/TCP may appear against every host as: `closed`. This is not a firewall misconfiguration. [This documentation](https://kb.fortinet.com/kb/documentLink.do?externalID=FD48365) details more on this issue.
* When a port appears as `open|filtered` after performing a UDP scan, try running `nmap -sUC -p [PORT] [IP_Address]` to verify if it is open.
