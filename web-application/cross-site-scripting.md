# Cross-Site Scripting (XSS)

### Description

> Cross-Site Scripting (XSS) attacks are a type of injection, in which malicious scripts are injected into otherwise benign and trusted websites. XSS attacks occur when an attacker uses a web application to send malicious code, generally in the form of a browser side script, to a different end user. Flaws that allow these attacks to succeed are quite widespread and occur anywhere a web application uses input from a user within the output it generates without validating or encoding it.

{% embed url="https://owasp.org/www-community/attacks/xss/" %}

### Going Beyond 'Document.Cookie'

While using `document.cookie` is great to demonstrate the exploitability of a Cross-Site Scripting vulnerability, to further demonstrate the risk we can leverage the following resources:

* [BeEF](https://beefproject.com)
* [XSShell](https://github.com/raz-varren/xsshell)

{% embed url="https://infosecwriteups.com/stored-xss-to-account-takeover-going-beyond-document-cookie-970e42362f43" %}

### Why HttpOnly Isn't Enough

There are multiple articles on the Internet stating that the `HttpOnly` flag provides a false sense of security as an attacker is unlikely to wait several hours for a user to trigger the payload and obtain a session token. Rather, an attacker can leverage a more sophiscated attack to hook the user or perform immediate malicious actions.

```http
# This is the flag we are talking about
Set-Cookie: SESSIONID=[token]; HttpOnly
```

{% embed url="https://www.gnucitizen.org/blog/why-httponly-wont-protect-you/" %}

{% embed url="https://portswigger.net/kb/issues/00500600_cookie-without-httponly-flag-set" %}

### Testing / Payload Creation

{% embed url="https://portswigger.net/web-security/cross-site-scripting/cheat-sheet" %}

{% embed url="https://jsfiddle.net" %}

{% embed url="http://www.jsfuck.com" %}

{% embed url="https://ppn.snovvcrash.rocks/pentest/web/xss" %}

{% embed url="https://xssor.io" %}
