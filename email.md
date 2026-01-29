JENKINS EMAIL NOTIFICATION USING GMAIL SMTP (NEGATIVE CASE)

Since I am using GitHub plugin with Poll SCM, Jenkins keeps checking the repository again and again, which is expensive.

To handle negative cases (like build failure), I configured email notifications in Jenkins so that I get notified automatically.

SMTP CONFIGURATION IN JENKINS

SMTP Server:
smtp.gmail.com

Security:
• SSL enabled
• Port: 465

This configuration allows Jenkins to send emails using Gmail securely.

GMAIL ACCOUNT REQUIREMENT (IMPORTANT)

To use Gmail SMTP with Jenkins:

• A Gmail account is required
• 2-Step Verification (2FA) must be enabled on the Gmail account

Without 2FA, Gmail will NOT allow app-based SMTP access.

GENERATING APP PASSWORD (GOOGLE SIDE)

Steps performed:

Open Manage Google Account

Go to the Search bar

Search for App passwords

Create a new app password

Give any name (for example: Jenkins)

Google generates a password automatically

This password is NOT the Gmail password.

ADDING CREDENTIALS IN JENKINS

In Jenkins email configuration:

• Username: Gmail email ID
• Password: App password generated from Google

The app password is copied from Google and pasted into Jenkins.

WHY APP PASSWORD IS USED

• Gmail does not allow normal password for SMTP
• App password is secure and limited
• Used only for Jenkins email notifications

USE CASE (NEGATIVE SCENARIO)

With this setup:

• Jenkins sends email when a build fails
• Useful when Poll SCM pulls faulty code
• No need to check Jenkins dashboard manually

KEY LEARNINGS

• Poll SCM is expensive as Jenkins keeps polling GitHub
• Email notification helps in failure monitoring
• Gmail SMTP requires 2FA enabled account
• App password is mandatory for Jenkins
• Username is Gmail ID, password is app password

This completes email notification setup for Jenkins negative case.