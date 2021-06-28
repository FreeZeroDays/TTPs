# Enum4Linux - Grep Magic for Usernames
1. Grep out usernames in no order:
2. `cat usernameenum.txt | grep "user" | awk {'print $1'} | cut -d '[' -f 2 | cut -d ']' -f 1 > FinalUsernameList.txt`

1. Sort alphabetically and delete duplicates:
2. `cat usernameenum.txt | grep "user" | awk {'print $1'} | cut -d '[' -f 2 | cut -d ']' -f 1 | sort -u -k > FinalUsernameList.txt`
