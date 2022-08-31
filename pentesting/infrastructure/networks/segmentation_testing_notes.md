---
description: >-
  When performing segmentation tests for PCI compliance, there aside from my
  Nmap scans there are a few things I've wanted to keep jotted down. This
  section contains my notes.
---

# Segmentation Testing Notes

### Basic Checks

Below are some basic commands to use while performing segmentation testing.\
It should be noted that these should be modified in order to be more thorough.&#x20;

#### &#x20;ICMP

```bash
nmap -sn $subnet -oA ICMP_Check
```

#### TCP

```bash
nmap -sS -Pn -p- $subnet -oA TCP_Scan 
```

#### UDP

```bash
nmap -sU -Pn --top-ports 1000 $subnet -oA UDP_Scan
```

#### IPv6

```bash
nmap -6 $ipv6address -oA IPv6_Scan
```

### Notes

* When performing a segmentation test against FortiGate devices, port 113/TCP may appear against every host as: `closed`. This is not a firewall misconfiguration. [This documentation](https://kb.fortinet.com/kb/documentLink.do?externalID=FD48365) details more on this issue.
* When a port appears as `open|filtered` after performing a UDP scan, try running the following to verify if it is open:

```bash
nmap -sUC -p $port $ipaddress
```

{% hint style="warning" %}
Segmentation tests should note **all** open ports regardless of the business use case. If a business needs a port open, jusitifcation should be provided in the report.
{% endhint %}
