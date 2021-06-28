Recently on an engagement I had a request from a client who wanted to be provided with only "In-Scope" hosts that were in the Responder-logs. 
This is because they wanted an actionable list of hosts to remediate in retesting rather than "the entire domain is impacted", pls fix because you can be owned in 30 seconds. 
With how Responder works, it's not unlikely for a host that is "out of scope" to be in the logs. 
If this is ever an ask, I found out a pretty easy way to grep out hosts from IPs within scope and provide this ask to a client. 

1. Place the hosts in-scope hosts into a file. For this example, it will be titled `InScopeHosts.txt`

2. Grep out the Responder-Session log to only IP Addresses:
`cat Responder-logs | grep -o '[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}’ ResponderIPs.txt`

3. Compare the two files with grep. This command will pipe duplicate IPs between the files into a new one.
`egrep "`cat InScopeHosts.txt|xargs -I {} echo -n '|{}'|sed -e 's/^|//'`” ResponderIPs.txt > RepeatedIPs.txt`

4. Remove duplicates from the files using Excel (I find this easiest since I'll paste it into a report, but sort also works)

If the client has provided /24s then break these into smaller lists via your choice of tool. 
`nmap -sL -n 127.0.0.0/24 | awk '/Nmap scan report/{print $NF}’`
