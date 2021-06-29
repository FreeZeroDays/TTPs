# Just some small notes on tunneling, these are specific to my engagement use case where I go Tester --> Jumpbox --> Client Machine

Accessing a specific port through the jumpbox (used when my proxy dies for some reason)
1. `ssh -i .ssh/ssh-jumpbox-20191202.pem -A -t ubuntu@34.219.107.198 -L 8834:localhost:8834`
2. `ssh -A -t -l root localhost -p2222 -L 8834:localhost:8834`
