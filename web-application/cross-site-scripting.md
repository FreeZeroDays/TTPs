# Cross-Site Scripting (XSS)

### Description

> Cross-Site Scripting (XSS) attacks are a type of injection, in which malicious scripts are injected into otherwise benign and trusted websites. XSS attacks occur when an attacker uses a web application to send malicious code, generally in the form of a browser side script, to a different end user. Flaws that allow these attacks to succeed are quite widespread and occur anywhere a web application uses input from a user within the output it generates without validating or encoding it.

{% embed url="https://owasp.org/www-community/attacks/xss/" %}

### Going Beyond 'Document.Cookie'

While using `document.cookie` is great to demonstrate the exploitability of a Cross-Site Scripting vulnerability, to further demonstrate the risk we can leverage the following resources:

* [BeEF](https://beefproject.com)
* [XSShell](https://github.com/raz-varren/xsshell)

{% embed url="https://infosecwriteups.com/stored-xss-to-account-takeover-going-beyond-document-cookie-970e42362f43" %}

### Payloads

{% embed url="https://jsfiddle.net" %}

{% embed url="http://www.jsfuck.com" %}

{% embed url="https://ppn.snovvcrash.rocks/pentest/web/xss" %}

{% embed url="https://xssor.io" %}
