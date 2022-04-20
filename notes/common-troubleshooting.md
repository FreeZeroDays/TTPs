---
description: Commands used for troubleshooting various issues.
---

# Common Troubleshooting

#### Fix Invalid Signature During apt-update

```bash
gpg --keyserver pgpkeys.mit.edu --recv-key ED444FF07D8D0BF6
gpg -a --export ED444FF07D8D0BF6 | sudo apt-key add -
```

#### Fix Kirbi2John Issues:

```bash
sudo apt-get install gcc python-dev libkrb5-dev
```

#### Fixing SMB Share Issues

Fix the following error by running: `client min protocol = NT1`

```bash
do_connect: Connection to 10.11.1.136' failed (Error NT_STATUS_UNSUCCESSFUL)
```
