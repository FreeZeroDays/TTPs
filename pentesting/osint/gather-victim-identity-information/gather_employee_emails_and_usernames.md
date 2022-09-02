---
description: MITRE ATT&CK, Reconnaissance, Sub-technique T1589.002
---

# Email Addresses

### Popular Go-to Locations

* [Hunter.io](https://hunter.io)
* [Phonebook.cz](https://phonebook.cz)
* [ZoomInfo](https://www.zoominfo.com)
* Data breaches (self promotion, use my tool breach-rip to parse these fast)

### Using Tools Available on GitHub

* [Linkedin2Username](https://github.com/initstring/linkedin2username)
* [BridgeKeeper](https://github.com/0xZDH/BridgeKeeper)
* [Peasant](https://github.com/arch4ngel/peasant)
* [LinkedInt](https://github.com/vysecurity/LinkedInt)

### Creating Username Lists

Once we have identified a list of employee names, we can place them into a list to use throughout the engagement in multiple phases.

Below are my personal recommendations:

1. Identify the username schema that the organization uses.
2. Collect emails from Hunter.io, Data breaches, Phonebook, etc
3. Run tooling against LinkedIn, Google, etc
4. Run BridgeKeeper against any names identified to place them into the correct format.
5. Place all of the identified usernames into a file and run `sort -u` to clean up the file.
6. Verify these against the domain controller if possible, alternatively utilize all of these emails in external phishing campaigns.

### Helpful Commands to Create a List

#### Grep a list of emails from a .JSON or other file:

```bash
grep -E -o "\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,6}\b" file.txt
```

#### Quick awk magic to add “@client.com” after every username:

```bash
awk '{print $0 "@client.com"}' usernames.txt > emails.txt
```

#### Quick sed magic to remove "@client.com" after every email:

```bash
sed 's/@.*//' emails.txt > usernames.txt
```
