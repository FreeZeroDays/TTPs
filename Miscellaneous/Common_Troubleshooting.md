---
description: >-
  Commands I commonly use for troubleshooting various installation or tool
  issues.
---

# Common Troubleshooting

### Fix Invalid Signature when Performing Apt-Update

`gpg --keyserver pgpkeys.mit.edu --recv-key ED444FF07D8D0BF6`\
`gpg -a --export ED444FF07D8D0BF6 | sudo apt-key add -`

### Get Wine32 Working on Latest Version of Kali

`sudo dpkg --add-architecture i386 && sudo apt-get update && sudo apt-get install wine32`

### Fix Kirbi2John Run Issues

`sudo apt-get install gcc python-dev libkrb5-dev`
