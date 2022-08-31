# TCPDump

### Capture

Capture on eth0, all ports, and write to `capture.pcap`

```bash
sudo tcpdump -i eth0 -w capture.pcap
```

This pcap can then be analyzed further with Wireshark or input to PCredz and/or Network Miner.&#x20;

### References

{% embed url="https://www.hackingarticles.in/comprehensive-guide-to-tcpdump-part-1/" %}

{% embed url="https://www.blackhillsinfosec.com/getting-started-with-tcpdump/" %}
