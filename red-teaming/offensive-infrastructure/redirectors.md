# Redirectors

A redirector is essentially a relay server that sits in between the attacker and the victim machine. When the attacker sends a command to the redirector, it forwards the command to the victim machine. Similarly, when the victim machine sends data back to the attacker, it goes through the redirector, which then forwards the data to the attacker.

A redirector helps us to evade the blue team and ensure that we burn the redirector instead of other parts of our infrastructure that potentially take longer to setup (Phishing server, C2, etc.)

### The "Dumb" Redirector

Socat functions as a "dumb redirector" in the sense that they listen on the specified network interface and port, forwarding **all** traffic received to a listener port on the team server.

This doesn't provide the greatest hardening for our attack infrastrucutre and may lead to our infrastructure getting burned faster than we anticipated. The following command can be used to setup a dumb redirector with Socat:

```bash
socat TCP4-LISTEN:80,fork TCP4:10.5.5.5:80
```

Additionally, we can also configure a dumb redirector by using IPTABLES as demonstrated in the following command:

```bash
# In this example we are forwarding all traffic from our host to 10.5.5.5.5.
iptables -I INPUT -p tcp -m tcp --dport 80 -j ACCEPT
iptables -t nat -A PREROUTING -p tcp --dport 80 -j DNAT --to-destination 10.5.5.5:80
iptables -t nat -A POSTROUTING -j MASQUERADE
iptables -I FORWARD -j ACCEPT
iptables -P FORWARD ACCEPT
sysctl net.ipv4.ip_forward=1
```

### Getting Smart (Redirector)

When setting up infrastructure for a red team operation, I would recommend going the smarter route and leveraging the `.htaccess` file and Apache's `mod_rewrite`.&#x20;

When writing custom rules for your redirector, I would recommend the following blog post:

{% embed url="https://bluescreenofjeff.com/2016-06-28-cobalt-strike-http-c2-redirectors-with-apache-mod_rewrite/" %}

Additionally, the below is an excerpt from that blog post on example rules to be placed in `.htaccess`. This ensures that only requests made with the specific `HTTP_USER_AGENT` specified will be forwarded to your team server, all other traffic will be redirected.

```bash
RewriteEngine On
RewriteCond %{REQUEST_URI} ^/(metro91/admin/1/ppptp.jpg|metro91/admin/1/secure.php)/?$
RewriteCond %{HTTP_USER_AGENT} ^Mozilla/4\.0\ \(compatible;\ MSIE\ 6\.0;\ Windows\ NT\ 5\.1;\ SV1;\ InfoPath\.2\)?$
RewriteRule ^.*$ http://TEAMSERVER-IP%{REQUEST_URI} [P]
RewriteRule ^.*$ http://example.com/? [L,R=302]
```

### References

{% embed url="https://www.ired.team/offensive-security/red-team-infrastructure/redirectors-forwarders" %}

{% embed url="https://synzack.github.io/C2-Redirection-for-Offensive-Operations/" %}

{% embed url="https://thevivi.net/blog/infrastructure/2017-11-03-securing-your-empire-c2-with-apache-mod-rewrite/" %}

{% embed url="https://bluescreenofjeff.com/2018-04-12-https-payload-and-c2-redirectors/" %}
