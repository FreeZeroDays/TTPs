---
description: >-
  This section briefly describes how to create templates for use in phishing
  campaigns. This advice is not specific to one phishing framework.
---

# Creating Templates

## Gathering the Details

Begin by gathering the information relevant to your campaign

* **Name** - Think of a name for your template. This will come in useful when identifying it in the future. Especially if this is a generic phishing campaign that will be reused (E.g.,Important Updates on Employee Dress Code)
* **Subject** - Give the template a subject title. This should be something engaging that the end-user will want to click on.
* **Sender** - Provide a name for the user or organization that the email is simulating. This could be something as simple as \[COMPANY] to a specific user working at the company you're impersonathing e.g., \[John Doe]

## Building the Template

This may be the hardest part of your day. Creating a convincing pretext that will convince the target to click a link or download a document.

Thankfully there are several repositories available online with templates and pretext ideas that are ready to go:

* [Pre-text\_Project](https://github.com/pretext-project/pretext-project.github.io/tree/master/\_pretexts)
* [GoPhish-Templates](https://github.com/DeviantSec/GoPhish-Templates)

The following details a template that I've used previously. The landing page was a link to the employee login where after credentials were entered where once I successfully landed a phish I could access the employee portal and attempt credential stuffing throughout the environment.

```markup
<html>
<head>
	<title></title>
</head>
<body>
<div align="center"><img 
[SNIP]
<p><font face="Verdana">Dear {{.Email}},&nbsp;</font></p>

<p><font face="Verdana"><font face="Verdana">You&#39;ve received a package! Your company has enrolled you in Your Package Pickup to simplify the mailroom process and get your package to you fast!</font></font></p>

<p><font face="Verdana"><font face="Verdana">The details of your package are as follows:</font></font></p>

<p><font face="Verdana"><font face="Verdana"><strong>Type</strong>: Parcel<br />
<strong>Carrier</strong>: Fed Ex<br />
<strong>Tracking Number</strong>: 231300687629630<br />
<strong>Method</strong>: 2-Day Express Saver<br />
<strong>Origin</strong>: Cincinnati, OH</font></font></p>

<p><font face="Verdana"><font face="Verdana">TO get started, you&#39;ll need to log into your account. It only takes a minute to get going - you can use your corporate e-mail credentials to log in.</font></font></p>

<p><font face="Verdana"><font face="Verdana">Set up your account now!<br />
Your Username: {{.Email}}<br />
<a href="{{.URL}}">https://www.yourpackagepickup.com/pickup</a></font></font></p>

<p><br />
<font face="Verdana"><font face="Verdana">Once you&#39;ve set up your account online, you&#39;ll select how you&#39;d like to receive your package. It&#39;s really that easy!</font></font></p>

<p><font face="Verdana"><font face="Verdana">Let us know if you have any issues with your shipment at {{.URL}}.</font></font></p>

<p><br />
<font face="Verdana"><font face="Verdana">Best,&nbsp;<br />
Your Package Pickup Care Team<br />
hello@yourpackagepickup.com</font></font></p>

<p><br />
<font face="Verdana"><font face="Verdana">Copyright 2019 YourPackagePickup. All rights reserved.<br />
&nbsp;</font></font></p>

<p><font face="Verdana">{{.Tracker}}</font></p>
</body>
</html>
```
