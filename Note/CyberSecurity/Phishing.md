- When emails are sent to a target(s) purporting to be from a trusted entity to lure individuals into providing sensitive information
- it is the subset of social engineering
- communication medium is mostly message
- most common phishing happens via email
- the spread of internet has spread phishing to short text message (smishing), voice call (vishing), QR codes(quishing) and social media DM's
- purpose: to make user click, open or reply to a message so attacker can steal information

### Defeating Phishing with S.T.O.P method
First S.T.O.P
**S**uspicious
**T**elling me to do something?
**O**ffering me something
**P**ushing me to do something

Second S.T.O.P.
**S**low down: scammer run on our adrenaline
**T**ype the address yourself: Don't use the message link
**O**pen nothing unexpected: verify first
**P**rove the sender: check the real address not only the display name

### Building the Phishing trap
- A phishing attack must be convincing to succeed from a penetration tester’s perspective
- Effectiveness depends on both message content and trap setup, not just writing
- The phishing trap is designed based on the attacker’s objectives
- Research on the target influences how the trap is created
- One method is attaching a malicious file to compromise the target’s machine
- Another method is creating a fake login webpage to steal credentials

### Performing a Phishing attack via `setoolkit`
- Once the phishing page is ready, the next step is delivering it via a realistic-looking phishing email
- Sending emails from a personal address is ineffective; the sender should appear legitimate and trusted by the target
- The realism of the sender, subject, and context increases the chance of the target falling for the phishing attempt
- A challenge is delivering a believable email that includes a link to the fake login page
- The Social-Engineer Toolkit (SET) can be used to create and send phishing emails
- SET is an open-source tool designed for social engineering scenarios
- It provides features such as composing and sending phishing emails
- In this scenario, SET is used specifically to send a phishing email to the target user
- SET is launched from the terminal using:  `setoolkit`
- From the main menu, option 1 is selected to choose Social-Engineering Attacks
- From the next menu, option 5 is selected to choose Mass Mailer Attack
- From the mass mailer options, option 1 is selected to send an email to a single address
- The tool prompts for email delivery configuration details
- The target email address is specified
- Email delivery is set to use an own server or open relay
- A trusted-looking sender email and sender name are chosen
- Open-relay username and password fields are left blank
- The SMTP server address is provided
- The default SMTP port 25 is used
- Additional email options are configured
- The email is not flagged as high priority
- No file or inline attachment is included
- A convincing email subject is chosen
- The message is sent as plaintext
- A realistic message body is written
- The phishing URL is included in the message
- The message body is ended by typing:  `END`
- SET sends the phishing email and confirms completion
- After sending, the attacker monitors the phishing server terminal
- Credentials may appear after waiting 1–2 minutes if the target interacts with the phishing page
