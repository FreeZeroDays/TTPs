---
description: >-
  Collection of Bug Bounty tips & tricks I have discovered and/or read on
  Twitter. Little bit of an overlap with web application testing but less
  vulnerability focused.
---

# Bug Bounty Tips & Tricks



1. When crawling a target and observing the "node\_modules" directory, make sure to verify each one of those modules being used has a public namespace associated with it (dependency confusion).
   1. [https://snyk.io/blog/detect-prevent-dependency-confusion-attacks-npm-supply-chain-security/](https://snyk.io/blog/detect-prevent-dependency-confusion-attacks-npm-supply-chain-security/)
2. Leverage `xmlrpc.php` with the `pingback.ping` command to discover a sites Origin IP address. Then supply it in the `Host:` header to bypass an in place rate limit.
3. Use one of the following extensions to open several URLs in your browser (ultimately adding them to your Interception Proxy), this can be better than using EyeWitness when there's redirect/CDN issues:
   1. [https://chromewebstore.google.com/detail/openlist/nkpjembldfckmdchbdiclhfedcngbgnl?hl=en](https://chromewebstore.google.com/detail/openlist/nkpjembldfckmdchbdiclhfedcngbgnl?hl=en)
   2. [https://addons.mozilla.org/en-US/firefox/addon/openlist/](https://addons.mozilla.org/en-US/firefox/addon/openlist/)
4. Configure Burp to display "hidden fields in forms" during proxying.
5. Create your own wordlists. Use SecLists as a starting point and leverage personal research + GAP to create personal and customized wordlists. This is your secret sauce during engagements.
6. `/.well-known/apple-app-site-association` often times contains "weird" endpoints specified by a developer.
7. Refer to the following tweet from Jason Haddix on exploring parameter fuzzing using ffuf: [https://twitter.com/Jhaddix/status/1735337603027685605](https://twitter.com/Jhaddix/status/1735337603027685605) (can also use these wordlists with param miner)
   1. [https://github.com/danielmiessler/SecLists/blob/master/Discovery/Web-Content/burp-parameter-names.txt](https://github.com/danielmiessler/SecLists/blob/master/Discovery/Web-Content/burp-parameter-names.txt)
   2. [https://github.com/g0ldencybersec/sus\_params/blob/main/txt/debug.txt](https://github.com/g0ldencybersec/sus\_params/blob/main/txt/debug.txt)
8. Great general bug bounty methodology on using OpenList, GAP, and Burp Suite: [https://twitter.com/nullenc0de/status/1701318185352417648](https://twitter.com/nullenc0de/status/1701318185352417648)
9. Bug Bounty 'oneliner' for JSRecon:  ([https://twitter.com/nullenc0de/status/1680233695959998464](https://twitter.com/nullenc0de/status/1680233695959998464))

```
echo "https://coastlinecyber.com" | subjs | while read -r url; do jsluice urls -R "$url" <(curl -sk "$url"); done | jq -r '.url' |qsreplace -a 
```

Chain with the following to identify potential XSS vulnerabilities:

```
cat sub_root.txt | subfinder -silent | dnsx -silent | httpx -silent | subjs | while read -r url; do jsluice urls -R "$url" <(curl -sk "$url"); done | jq -r '.url' | qsreplace -a | grep = | kxss
```

10. One liner for sorting per vulnerability with tomnomnom's `gf` tool:

```
cat url_queries.txt | gf xss | sed 's/=.*/=/' |  sed 's/URL: //' | tee xssout.txt
```

11. One liner for automating testing for blind xss using dalfox, note, should be paired with the command above:

```
dalfox file xssout.txt -b <blindXSSpayload> -o dalfox.txt
```

12. One liner for reconaissance, `hosts.txt` should be full of all subdomains identified, we will then ultimately grep out all URLs and paths for further fuzzing with ffuf after:

```
cat hosts.txt | gospider -S - --depth 1 -v -t 50 -war -c 10 -o output
cd output
cat * | grep -Eo "(http|https)://[a-zA-Z0-9./?=_%:-]*" | sort -u > endpoints.txt
cat endpoints.txt | python3 getdirs.py -s -o dirs.txt
```

13. Proxy your tooling through BurpSuite for better results. For example, proxying GoSpider: `gospider -S live-urls -a -w -r --sitemap -c 20 -d 8 -p http://127.0.0.1:8080`

### References

{% embed url="https://twitter.com/ArchAngelDDay/status/1661924038875435008" %}
