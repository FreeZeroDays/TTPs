# Phishing Methodology

1. Reconnaissance 
  i. Identify the target domain. This is often specified in the scope of the engagement. 
  ii. Use OSINT to identify emails and victims to receive your phish. 
    a. Publicly available tools such as LinkedIn2Username, BridgeKeeper, previously pwned databases, Phonebook.cz, etc. are great for this.
  iii. Enumerate the targets domain. Search for blogs, company calendars, company specific portals, enumerate subdomains. All of this information is going to assist you when creating your campaign.
2. Prepare the Campaign
  i. Identify and purchase an available domain to be used for your campaign.
  ii. Lookalike domains can either be manually created or found with tools such as CatPhish. Additionally, domains with a good reputation can be identified from sites similar to expireddomains. 
  iii. Create a convincing template. This involves creating the subject, sender, and content of the email. Additionally, this is where you would decide if you need to create a landing page or will be attaching a malicious document to the email.
    a. There are several repositories on my GitHub and scattered throughout the Internet with ideas for pretexts and campaigns. 
    b. The best type of campaign reference are the ones you receive! Check your spam emails and see if anything can be modified, improved, and sent out!
    c. When creating a malicious document there are multiple tools avaialble such as SET and GitHub that can create a wide variety of documents with payloads embedded.
    d. Create a landing page. This can be based off of the company specific logan portals during the reconnaissance phase or a commonly used login portal such as Exchange.
3. Prepare the Infrastructure
  i. Setup the purchased domain to be used in the campaign, this is extremely easy to configure in GoPhish.
  ii. Configure the sending profile to use an SMTP server such as SES or SendGrid to bypass protections in palce.
  iii. Harden the GoPhish infrastructure by changing the email headers.
  iv. Configure the email service to have the appropriate SPF, DMARC, and DKIM records
    a. This is mostly important if you are trying to bypass protections in place. This should not impact authorized phishing exercises where the client whitelists you.
4. Testing the Campaign
  i. Test the campaign by sending an email to mail-tester. This site will alert you if there is anything misconfigured or give you tips on how to improve your credibility. 
  ii. I would advise against testing via something like your own Outlook or Gmail. If your email is flagged it is possible that your domain could be marked as spam and blacklisted.
  iii. When testing your email - double check your pretexts and landing page look correct/are working as intended.
5. Launch the Campaign 
  i. Monitor the status of your campaign. You should start seeing clicks come in. A click tells us a few different things about the victim:
    a. The email was successfully received by the victim.
    b. The email was opened.
    c. The user is active.
