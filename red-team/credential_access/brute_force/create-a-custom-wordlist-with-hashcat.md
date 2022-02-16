---
description: >-
  Often times it is beneficial to create a custom wordlist to be used in
  credential attacks
---

# Create a Custom Wordlist with Hashcat

#### Create a simple wordlist or run cewl:

```
Acme (Domain)
Autumn
Winter
Spring
Summer
Welcome
```

#### Use Hashcat to Create a Custom Wordlist

`hashcat --force custom -r /usr/share/hashcat/rules/best64.rule --stdout > wordlist`
