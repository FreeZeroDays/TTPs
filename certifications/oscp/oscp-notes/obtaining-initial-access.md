---
description: Rough notes on obtaining initial access
---

# Obtaining Initial Access

### Initial Access

* Always try to login with default passwords and with using the username as a password. For example, if a username has been identiifed as `parzival` try and login with the password `parzival`
  * Also apply this in reverse. If you have identified a password then attempt to use it on any newly discovered usernames.
* Sometimes a simple wordlist can be your friend.. Ensure dumb combinations are attempted  like `admin:admin`
* If testing for Shellshock on SMTP then I have found[ this exploit ](https://github.com/3mrgnc3/pentest\_old/blob/master/postfix-shellshock-nc.py)to be the most reliable. It requires a valid email address so ensure you run `VRFY` to enumerate a valid email prior to execution.
* If you can access the Apache logs through LFI and observe the 'User Agent' is viewable, we can potentially specify our user agent to PHP code and execute that on the target machine. [This video from John Hammond](https://www.youtube.com/watch?v=u\_uuk7FWWF4) is a great example.
  * Using this we can potentially turn an LFI into RCE. An example user agent would be the following: `User-Agent: <?php system(\$_GET['c']); ?>`
* Log into the SMTP server to identify the version if it is not returned in the Nmap scan. Identifying Postfix means that multiple exploits from Searchsploit may work: `searchsploit postfix`
* Narrowing down a version number of an application can greatly increase your chances of finding an exploit.&#x20;
* If you ever have LFI and SSH is open, try reading the `id_rsa` file for any users that have been enumerated.
