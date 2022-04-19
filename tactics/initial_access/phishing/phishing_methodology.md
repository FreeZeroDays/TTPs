# Phishing Methodology

1. **Setting up GoPhish**
   1. Setting up GoPhish is extremely easy. Simply grab the binary from the official [GoPhish GitHub](https://github.com/gophish/gophish) and execute it in a tmux session:

```bash
tmux new-session -d -s "GoPhish" ./gophish
```

1. **Reconnaissance**
   1. Identify the target domain. This is often specified in the scope of the engagement.
   2. Use OSINT to identify emails and victims to receive your phish.
      1. Publicly available tools such as [LinkedIn2Username](https://github.com/initstring/linkedin2username), [BridgeKeeper](https://github.com/0xZDH/BridgeKeeper), previously pwned databases, [Phonebook.cz](https://phonebook.cz), etc. are great for this.
   3. Enumerate the targets domain. Search for blogs, company calendars, company specific portals, enumerate subdomains. All of this information is going to assist you when creating your campaign.
2. **Prepare the Campaign**
   1. Identify and purchase an available domain to be used for your campaign.
      1. Lookalike domains can either be manually created or found with tools such as [CatPhish](https://github.com/ring0lab/catphish). Additionally, domains with a good reputation can be identified from sites similar to expireddomains.
   2. Create a convincing template. This involves creating the subject, sender, and content of the email. Additionally, this is where you would decide if you need to create a landing page or will be attaching a malicious document to the email.
      1. There are several repositories on my GitHub and scattered throughout the Internet with ideas for pretexts and campaigns.
      2. The best type of campaign reference are the ones you receive! Check your spam emails and see if anything can be modified, improved, and sent out!
      3. When creating a malicious document there are multiple tools avaialble such as [LuckyStrike](https://github.com/curi0usJack/luckystrike) and [BoobSnail](https://github.com/STMCyber/boobsnail) that can create a wide variety of documents with payloads embedded.
      4. Create a landing page. This can be based off of the company specific logan portals during the reconnaissance phase or a commonly used login portal such as Exchange.
3. **Prepare the Infrastructure**
   1. Setup the purchased domain to be used in the campaign, this is extremely easy to configure in GoPhish.
   2. Configure the sending profile to use an SMTP server such as SES or [SendGrid](https://sendgrid.com) to bypass protections in palce.
   3. Harden the GoPhish infrastructure by changing the email headers.
   4. Configure the email service to have the appropriate SPF, DMARC, and DKIM records
      1. This is mostly important if you are trying to bypass protections in place. This should not impact authorized phishing exercises where the client whitelists you.
4. **Testing the Campaign**
   1. Test the campaign by sending an email to [mail-tester](https://www.mail-tester.com). This site will alert you if there is anything misconfigured or give you tips on how to improve your credibility.
   2. I would advise against testing via something like your own Outlook or Gmail. If your email is flagged it is possible that your domain could be marked as spam and blacklisted.
   3. When testing your email - double check your pretexts and landing page look correct/are working as intended.
5. **Launch the Campaign**
   1. Monitor the status of your campaign. You should start seeing clicks come in. A click tells us a few different things about the victim:
      1. The email was successfully received by the victim.
      2. The email was opened.
      3. The user is active.
