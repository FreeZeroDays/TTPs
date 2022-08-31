---
description: MITRE ATT&CK, Privilege Escalation, Sub-technique T1548.001
---

# Setuid and Setgid

### Description

Setuid is a Unix file flag that allows an executable to be run with the permissions of the file owner. It is often used to allow a user to perform tasks that would otherwise require privileged access.

Setgid is the same concept but instead applies to groups rather than users.&#x20;

Let's take a look at the following example:

```bash
-rwsr-sr-x 1 root root 122 May 14 22:25 thefile
```

setuid is indicated by the first s whereas setgid is indicated by the second s.&#x20;

### Setting Permissions

```bash
# Change the setsuid flag:
chmod u+s $file

# Change the setgid bit:
chmod g+s $file 

# Change both the setuid and setgid bit:
chmod +s $file 
```

### Locating SUID/SGID Binaries

```bash
# Locate suid and sgid-enabled files for the current user
find / -perm -u=s -type f 2>/dev/null
```

### Escalating Privileges

Escalating privileges with these bits greatly depends on the binary that we haev in our posession. One of my favorite ways to search for what an binary can do is by referencing GTFOBins:

{% embed url="https://gtfobins.github.io" %}

### References

{% embed url="https://antonyt.com/blog/2020-03-22/privilege-escalation-via-setuid#what-is-setuid" %}
