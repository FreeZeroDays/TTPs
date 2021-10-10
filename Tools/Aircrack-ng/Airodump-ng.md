# Airodump-ng

Airodump-ng is used for packet capturing of raw 802.11 frames and is particularly suitable for collecting WEP IVs (Initialization Vector) for the intent of using them with aircrack-ng.
If you have a GPS receiver connected to the computer, airodump-ng is capable of logging the coordinates of the found access points.

## Usage

Run airodump-ng - it should be noted that airmon-ng needs to be running first

* ```airodump-ng wlan1```

Target a specific BSSID and channel with airodum-ng and write the output to a file.

* ```airodump-ng --bssid [BSSID] -c [CHANNEL] -w [FILENAME] wlan1```

## References
* [Airodump-ng](https://www.aircrack-ng.org/doku.php?id=airodump-ng) - Manual for Airodump-ng
