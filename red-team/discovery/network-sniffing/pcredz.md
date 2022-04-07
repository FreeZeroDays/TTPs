---
description: Network sniffing with Pcredz for passive wins during offensive engagements.
---

# PCredz

[PCredz](https://github.com/lgandx/PCredz) is a tool developed by lgandx that can either live capture on an interface or parse a PCAP file to extract cleartext information such as logins via FTP, POP, HTTP, or SNMP Community Strings (and much more). Additionally, this tool will also extract credit card numbers which is perfect for PCI engagements, although I have not personally seen one being transmitted in the clear.&#x20;

### Installing

```bash
sudo apt install python3-pip && sudo apt-get install libpcap-dev && pip3 install Cython && pip3 install python-libpcap && git clone https://github.com/lgandx/PCredz

```

### Usage

#### Live Capture with PCredz

`sudo python3 Pcredz -i eth0 -v`

#### Parse a PCAP file with PCredz

`python3 Pcredz -f NetworkCapture.pcap`

#### Parse a directory of PCAPs with PCredz

`python3 Pcredz -d /tmp/PCAPs/`
