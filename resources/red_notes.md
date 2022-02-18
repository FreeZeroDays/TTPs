---
description: >-
  Notes from various penetration testing engagements and CTFs that I thought
  would be worth documenting.
---

# Offensive Security Notes



1. Search for whitelisted applications when looking to migrate and dump credentials. During a penetration test I was struggling to dump credentials with Kiwi as a PoC. Migrating into an AppSense application that is required to be whitelisted by endpoints can result in easy l00t. [This link](https://knowledge.broadcom.com/external/article/171640/dlp-endpoint-agent-causes-delays-when-fi.html) lists a few of the executables that I was able to migrate into with Meterpreter and proceed to execute Kiwi from, namely EMUser.exe.
2. Time to Live
   1. &#x20;TTL > 64 it is most likely a Linux box
   2. TTL > 128 it is most likely a Windows
   3. TTL < 128 then most likely some type of networking device.
3. Some quick notes on organizing tooling:
   * Download and place the tool into /opt/ (e.g., Aquatone).&#x20;
   * Execute the following command on the Aquatone binary: `ln -s /opt/aquatone/aquatone /usr/local/bin/aquatone`
