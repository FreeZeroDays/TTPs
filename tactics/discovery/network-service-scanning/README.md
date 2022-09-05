---
description: MITRE ATT&CK, Discovery, Technique T1046
---

# Network Scanning

### ARP Scanning

ARP is a protocol used to resolve a MAC address for the NIC that has been configured with an IP address. ARP requests are sent in cleartext, meaning that anyone on the broadcast domain can observe and record them. &#x20;

```bash
# Active scanning
arp-scan -I eth0 $subnet

# Passive reconaissance 
netdiscover -i eth0 -r $subnet -p
```

### Ping Sweeping

```bash
# Perform a ping sweep with Nmap
nmap -sn $subnet/24 -oA PingSweepHosts
```

### References

#### ARP Scanning

{% embed url="http://edublog.bitcrack.net/2016/09/scanning-network-using-netdiscover-arp.html" %}

{% embed url="https://www.blackhillsinfosec.com/analyzing-arp-to-discover-exploit-stale-network-address-configurations/" %}
