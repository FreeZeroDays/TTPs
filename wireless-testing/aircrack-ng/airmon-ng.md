---
description: >-
  This script can be used to enable monitor mode on wireless interfaces.
  Entering the airmon-ng command without parameters will show the interfaces
  status.
---

# Airmon-ng

## Usage

Place wireless interface into montior mode:

```bash
airmon-ng [start|stop] wlan1 [channel]
```

Show/check any processes that may interfere with the aircrack-ng suite:

```bash
airmon-ng [check|check kill]
```

Verify that the monitor mode interface is listening on the desired channel frequency:

```bash
iwlist wlan1mon [channel]
```

## References

* [Airmon-ng](https://www.aircrack-ng.org/doku.php?id=airmon-ng) - Manual for Airmon-ng
