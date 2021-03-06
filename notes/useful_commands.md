---
description: >-
  A collection of random commands that I've found useful throughout penetration
  testing and red team exercises.
---

# Useful Commands

### Organization

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

#### Sort Usernames Obtained from Enum4Linux&#x20;

```bash
cat usernameenum.txt | grep "user" | awk {'print $1'} | cut -d '[' -f 2 | cut -d ']' -f 1 | sort -u -f > UsernameList.txt
```

### SSH Specific

#### Hide yourself using SSHuttle:

```bash
sshuttle -r $uswr@$ip 0.0.0.0/0 -e "ssh -i $ssh_key" --exclude $ip -v --method tproxy
```

#### Add SOCKS to an Existing SSH Connection

```bash
<enter> ~C
-D 1080
```

#### Forward a Port on an Existing SSH Connection

```bash
<enter> ~C
-L 1337:localhost:1337
```
