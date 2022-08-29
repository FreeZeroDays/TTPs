# Personal

### wifite2

{% embed url="https://github.com/derv82/wifite2" %}

1\. Installation:

```bash
# Required Installation
git clone https://github.com/derv82/wifite2.git
cd wifite2
sudo python setup.py install

# Optional Installation
git clone https://github.com/ZerBea/hcxdumptool.git
sudo apt install libcurl4-openssl-dev libssl-dev -y
make
sudo make install
```

2\. Run `wifite2`:

```bash
wifite -e $ssid
```

### Cracking the Handshake

> Use hash mode 22000 to recover a Pre-Shared-Key (PSK). Length of a PSK can be 8 up to 63 characters

```bash
hashcat -m 22000 $handshake /usr/share/wordlists/rockyou.txt -w /usr/share/rules/OneRule.rule
```

### References

{% embed url="https://null-byte.wonderhowto.com/how-to/hack-wi-fi-cracking-wpa2-passwords-using-new-pmkid-hashcat-attack-0189379/" %}
