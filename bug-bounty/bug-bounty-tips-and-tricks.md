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



### References

{% embed url="https://twitter.com/ArchAngelDDay/status/1661924038875435008" %}
