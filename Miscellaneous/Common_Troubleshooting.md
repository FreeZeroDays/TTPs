# Common Troubleshooting

## Fix Invalid Signature when Performing Apt-Update

```gpg --keyserver pgpkeys.mit.edu --recv-key  ED444FF07D8D0BF6``` \
```gpg -a --export ED444FF07D8D0BF6 | sudo apt-key add -```
