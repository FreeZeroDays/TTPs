---
description: >-
  Airodump-ng is used for packet capturing of raw 802.11 frames and is
  particularly suitable for collecting WEP IVs (Initialization Vector) for the
  intent of using them with aircrack-ng.
---

# Airodump-ng

## Usage

Run airodump-ng - it should be noted that airmon-ng needs to be running first

```bash
airodump-ng wlan1
```

Target a specific BSSID and channel with airodum-ng and write the output to a file:

```bash
airodump-ng --bssid [BSSID] -c [CHANNEL] -w [FILENAME] wlan1
```

## References

{% embed url="https://www.aircrack-ng.org/doku.php?id=airodump-ng" %}
