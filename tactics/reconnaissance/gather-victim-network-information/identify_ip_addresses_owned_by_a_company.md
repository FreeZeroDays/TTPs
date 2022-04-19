---
description: MITRE ATT&CK Reconnaissance, Sub-technique T1590.005
---

# Gather IP Addresses

### Hurricane Electric Internet Services

[Hurricane Electric Internet Services](https://bgp.he.net) is a fast way to identify what company owns what IP

### SecurityTrails

[SecurityTrails](https://securitytrails.com) Another good site for verifying IP addresses and netblocks belonging to an organization

### NetBlockTool

[NetblockTool](https://github.com/NetSPI/NetblockTool) can be used to gather IP ranges, points of contact, and even netblocks belonging to your target’s subsidiaries

Basic usage&#x20;

```bash
python3 NetblockTool.py -v [COMPANY]
```

Extract ranges owned by the target company’s subsidiaries

```bash
python3 NetblockTool.py -v Company -s

```

### References

{% embed url="https://www.netspi.com/blog/technical/network-penetration-testing/netblocktool" %}

{% embed url="https://securitytrails.com/blog/identify-ip-ranges-company-owns" %}
