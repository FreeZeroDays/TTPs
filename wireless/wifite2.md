# wifite2

### Description

`wifite2` is a rewrite of the popular tool `wifite`, a Python script for auditing wireless networks. This tool makes hacking wireless networks as automated as it can get. wifite2 will run existing wireless tools to conduct attacks such as Pixie-Dust attacks, WPA Handshake Captures, PMKID Hash Captures, and attacks against WEP such as fragmentation and chop-chop.&#x20;

### Installation

```bash
git clone https://github.com/derv82/wifite2.git
cd wifite2
sudo python setup.py install
```

### Usage

Simple usage of wifite2 is the following:

```bash
wifite -e $ssid
```

### Notes

wifite2 has a list of optional but recommended tooling to install. I highly recommend installing these as attacks such as capturing `PMKID` hashes will not be possible without them.&#x20;

```bash
git clone https://github.com/ZerBea/hcxdumptool.git
sudo apt install libcurl4-openssl-dev libssl-dev -y
make
sudo make install
```

### References

{% embed url="https://github.com/derv82/wifite2" %}

{% embed url="https://null-byte.wonderhowto.com/how-to/hack-wi-fi-cracking-wpa2-passwords-using-new-pmkid-hashcat-attack-0189379" %}
