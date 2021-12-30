---
description: Quick greps to grab usernames from an Enum4Linux output.
---

# Grep Usernames

## Usage

1. Run the following command against a host to gather a list of usernames:

`enum4linux -U [TARGET]`

1. Run the following command to grep out usernames:

Grep out usernames, sort alphabetically, and delete duplicates

`cat usernameenum.txt | grep "user" | awk {'print $1'} | cut -d '[' -f 2 | cut -d ']' -f 1 | sort -u -f > UsernameList.txt`
