---
description: >-
  A collection of random commands that I've found useful throughout penetration
  testing and red team exercises.
---

# Useful Commands

Grep out a list of emails from a .JSON or other file:

```bash
grep -E -o "\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,6}\b" file.txt
```

Quick awk magic to add “@client.com” after every username:

```bash
awk '{print $0 "@client.com"}' usernames.txt > emails.txt
```

Quick sed magic to remove "@client.com" after every email:

```bash
sed 's/@.*//' emails.txt > usernames.txt
```

Hide yourself using SSHuttle:

```bash
sshuttle -r [USER]@[SERVER] 0.0.0.0/0 -e "ssh -i [SSH_KEY]" --exclude <server> -v --method tproxy
```
