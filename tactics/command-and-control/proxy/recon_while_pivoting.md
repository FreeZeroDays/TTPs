---
description: >-
  Some quick notes on performing discovery when working through proxychains or a
  beacon.
---

# Recon Through Proxychains

### Nmap Scanning with Proxychains

When performing scans on the network through proxychains it is important to use the `-sT` flag. The following command demonstrates an Nmap command to use:

```bash
nmap -sT -Pn -n $port
```

{% hint style="warning" %}
This may not be needed with SOCKS4 depending on your usecase. SOCKS5 supports ICMP and DNS which makes life considerably easier. &#x20;
{% endhint %}
