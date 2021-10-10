# Deauthenticate Clients

This attack sends disassocate packets to one or more clients which are currently associated with a particular access point.
Deauthenticating clients can be used for several attacks. Capturing WPA/WPA2 handshakes by forcing clients to reauthenticate is the most common.

## Usage

Run a deauthentication attack using aireplay-ng

* ```aireplay-ng -0 1 -a [ACCESS POINT MAC] -c [CLIENT MAC] wlan1mon```

## References
* [Deauthentication](https://www.aircrack-ng.org/doku.php?id=deauthentication) - Aircrack-ng manual on deauthentication
