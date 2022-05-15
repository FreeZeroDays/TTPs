# ARP Scanning

### Description

ARP is a protocol used to resolve a MAC address for the NIC that has been configured with an IP address. ARP requests are sent in cleartext, meaning that anyone on the broadcast domain can observe and record them. &#x20;

ARP is useful for reconaissance activities and can be done either passively or actively. While ARP can be used to perform poisoning attacks, simply understanding what is available on the network is sometimes more than enough.&#x20;

### Scanning

#### Active

```bash
arp-scan -I eth0 $subnet
```

#### Passive

```bash
netdiscover -i eth0 -r $subnet -p
```



### References

{% embed url="http://edublog.bitcrack.net/2016/09/scanning-network-using-netdiscover-arp.html" %}

{% embed url="https://www.blackhillsinfosec.com/analyzing-arp-to-discover-exploit-stale-network-address-configurations/" %}

{% embed url="https://www.youtube.com/watch?v=4xaWoZE8eik" %}
