Perfect — that detail matters 👍
Here is the **FINAL corrected version**, **plain text**, with **`vi` editor usage properly added** and **nano completely removed**.
Everything is now consistent with what you actually did.

---

JENKINS CI/CD LEARNING NOTES
(CentOS + VMware + Windows Host)

---

1. INTRODUCTION

I started learning Jenkins for CI/CD without any prior knowledge of Linux.
To practice Jenkins in a real environment, I set up two CentOS virtual machines using VMware.

System setup:
• Host OS: Windows
• Virtualization Tool: VMware
• Guest OS: CentOS

Virtual Machines:
• VM 1: Jenkins Server
• VM 2: Jenkins Client

Jenkins was installed on both CentOS systems for learning purposes.

---

2. BASIC UNDERSTANDING OF JENKINS

During installation and usage, I learned:

• Jenkins runs as a Linux service
• Jenkins is accessed using IP address and port
• Default Jenkins port is 8080
• Jenkins provides a web-based dashboard
• Jenkins can execute shell (bash) scripts

---

3. FINDING IP ADDRESS OF CENTOS

To access Jenkins, I first needed the IP address of the CentOS VM.

Command used:

ip addr

From the output, I noted the IPv4 address.

Jenkins access format:

http://<CENTOS_IP>:8080

---

4. FIRST-TIME JENKINS SETUP

When Jenkins runs for the first time, it asks for an initial admin password.

Jenkins shows a Linux file path similar to:

/var/lib/jenkins/secrets/initialAdminPassword

Command used to read the password:

cat /var/lib/jenkins/secrets/initialAdminPassword

Steps completed:
• Copied the password
• Pasted it into Jenkins UI
• Installed suggested plugins
• Created admin user
• Completed setup

---

5. JENKINS SERVICE MANAGEMENT COMMANDS

Jenkins service was managed using the following commands:

Start Jenkins:
systemctl start jenkins.service

Check status:
systemctl status jenkins.service

Stop Jenkins:
systemctl stop jenkins.service

---

6. MAKING JENKINS ACCESSIBLE FROM WINDOWS (OUTSIDE VM)

CentOS firewall blocks ports by default.

To access Jenkins from the Windows browser, I opened port 8080 using:

firewall-cmd --permanent --add-port=8080/tcp
firewall-cmd --reload

After this, Jenkins became accessible at:

http://<CENTOS_IP>:8080

---

7. CREATING DIRECTORY AND SCRIPT FILE

I created a temporary directory and a shell script file for Jenkins execution.

Commands used:

cd /tmp
mkdir jenkins-demo
cd jenkins-demo

Created the script file:

touch demo.sh

Provided execute permission:

chmod +x demo.sh

---

8. EDITING FILE USING VI EDITOR

I edited the script using **vi editor**.

Command used:

vi demo.sh

Steps inside vi editor:
• Pressed `i` to enter insert mode
• Wrote bash commands inside the file
• Pressed `Esc` to exit insert mode
• Typed `:wq` and pressed Enter to save and exit

(Using Shift + : + w + q)

Example script content:

#!/bin/bash
echo "Hello from Jenkins job"
date
whoami

---

9. TESTING SCRIPT MANUALLY

Before running it through Jenkins, I tested the script manually.

Command used:

bash demo.sh

The script executed successfully and displayed output.

---

10. CREATING FIRST JENKINS JOB

Steps performed in Jenkins UI:

• Clicked “New Item”
• Job name: Job-1
• Selected “Freestyle project”

Build configuration:
• Build Step → Execute Shell

Shell command used:

/tmp/jenkins-demo/demo.sh

Saved the job and clicked **Build Now**.

Result:
• Jenkins executed the script
• Output appeared in Console Output

---

11. ADDING PARAMETERS TO JENKINS JOB

I converted the job into a parameterized job.

Steps:
• Opened Job Configuration
• Enabled “This project is parameterized”
• Added “Choice Parameter”

Parameter details:
Name: ENVIRONMENT

Choices (each on a new line):

dev
test
prod

Important learning:
• Each choice must be on a new line
• Jenkins does not accept space-separated choices

---

12. USING PARAMETER IN BUILD STEP

I used the parameter inside the Jenkins shell build step.

Example command:

echo "Selected environment is: $ENVIRONMENT"

This showed how Jenkins passes parameters to shell scripts.

---

13. COMMANDS USED SUMMARY

Key Linux commands used:

ip addr
cat /var/lib/jenkins/secrets/initialAdminPassword
systemctl start jenkins.service
systemctl status jenkins.service
systemctl stop jenkins.service
firewall-cmd --permanent --add-port=8080/tcp
firewall-cmd --reload
cd
mkdir
touch
chmod +x
vi
./demo.sh

---

14. KEY LEARNINGS

• Jenkins runs on IP address + port
• Firewall configuration is required for external access
• Jenkins is managed as a Linux service
• vi editor is used to edit configuration/scripts
• Jenkins executes shell scripts
• Scripts should be tested manually before Jenkins execution
• Parameterized jobs allow dynamic input
• Choice parameters require newline-separated values

---

15. CONCLUSION

This hands-on Jenkins setup helped me understand Linux basics, Jenkins services, networking, and CI job execution.

It provided a strong foundation for learning advanced CI/CD pipelines.




ipconfig : shows the IP address and network details of the CentOS system

pwd : prints the present working directory (shows current folder path)

cat /var/lib/jenkins/secrets/initialAdminPassword : displays the initial Jenkins admin password stored in the file

systemctl start jenkins.service : starts the Jenkins service

systemctl status jenkins.service : shows the current status of the Jenkins service (running or stopped)

systemctl stop jenkins.service : stops the Jenkins service

firewall-cmd --permanent --add-port=8080/tcp : permanently allows incoming connections on port 8080 through the CentOS firewall

firewall-cmd --reload : reloads the firewall rules to apply the changes

mkdir jenkins-demo : creates a directory named jenkins-demo

cd jenkins-demo : changes the current directory to jenkins-demo

vi demo.sh : opens the file demo.sh in vi editor (creates the file if it does not exist)

bash demo.sh : runs the shell script using the bash interpreter