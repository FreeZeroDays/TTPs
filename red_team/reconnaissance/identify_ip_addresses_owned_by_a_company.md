---
description: This section lists multiple ways to identify IP addresses owned by a company
---

# Find IP Addresses Owned by a Company

## Hurricane Electric Internet Services

[Hurricane Electric Internet Services](https://bgp.he.net) is a fast way to identify what company owns what IP

## SecurityTrails

[SecurityTrails](https://securitytrails.com) Another good site for verifying IP addresses and netblocks belonging to an organization

## NetBlockTool

[NetblockTool](https://github.com/NetSPI/NetblockTool) can be used to gather IP ranges, points of contact, and even netblocks belonging to your target’s subsidiaries

Basic usage \\

`python3 NetblockTool.py -v [COMPANY]`

Extract ranges owned by the target company’s subsidiaries \\

`python3 NetblockTool.py -v Company -s`

## References

* [NetblockTool: The Easy Way to Find IP Addresses Owned by a Company](https://www.netspi.com/blog/technical/network-penetration-testing/netblocktool)
* [How to Find IP Ranges a Company Owns and Company IP addresses](https://securitytrails.com/blog/identify-ip-ranges-company-owns)
