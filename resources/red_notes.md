# Red\_Notes

1. Search for whitelisted applications when looking to migrate and dump credentials. During a penetration test I was struggling to dump credentials with Kiwi as a PoC. Migrating into an AppSense application that is required to be whitelisted by endpoints can result in easy l00t. [This link](https://knowledge.broadcom.com/external/article/171640/dlp-endpoint-agent-causes-delays-when-fi.html) lists a few of the executables that I was able to migrate into with Meterpreter and proceed to execute Kiwi from, namely EMUser.exe.
2. If the TTL is > 64 it is most likely a Linux box, if > 128 it is most likely a Windows and if it is < 128 then most likely some type of networking device.
