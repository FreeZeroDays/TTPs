# Just some small notes on tunneling, some of these are specific to my engagement use case where I go Tester --> Jumpbox --> Client Machine

Accessing a specific port through the jumpbox (used when my proxy dies for some reason)
1. `ssh -i .ssh/<KEY> -A -t <USER>@<IP> -L 8834:localhost:8834`
2. `ssh -A -t -l root localhost -p2222 -L 8834:localhost:8834`

Portfwd to Nessus on a Jumpbox 
1. `ssh <USER>@<IP> -L:31337:localhost:8834 -Nf`

Proxy with ProxyCap (Proxy running on Jumphost 1080 --> Internal Kali instance)
1. `ssh -i .ssh/<KEY> -fnNL 9999:127.0.0.1:1080 <USER>@<IP>`
