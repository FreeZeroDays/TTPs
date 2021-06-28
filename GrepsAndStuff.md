# Enum4Linux - Grep Magic for Usernames
* Grep out usernames in no order:
1. `cat usernameenum.txt | grep "user" | awk {'print $1'} | cut -d '[' -f 2 | cut -d ']' -f 1 > FinalUsernameList.txt`

* Sort alphabetically and delete duplicates:
1. `cat usernameenum.txt | grep "user" | awk {'print $1'} | cut -d '[' -f 2 | cut -d ']' -f 1 | sort -u -k > FinalUsernameList.txt`
