---
description: MITRE ATT&CK, Reconnaissance, Sub-technique T1589.002
---

# Gather Employee Email Addresses

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
