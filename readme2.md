JENKINS JOB SCHEDULING USING CRON (BUILD PERIODICALLY)

I learned how to schedule a Jenkins job to run automatically at fixed time intervals using the Build periodically option.

Steps performed:

Opened the Jenkins job configuration

Clicked on Build Triggers

Selected Build periodically

Entered the cron expression:

This cron expression means:
• The job runs every minute

BUILD STEP CONFIGURATION

Under Build → Execute Shell, I added a simple shell command:

echo "hello"

This command prints the word "hello" in the Jenkins console output.

RESULT

• Jenkins automatically runs the job every minute
• A new build is triggered without manual intervention
• Console output shows the echoed message each time

KEY LEARNING

• Jenkins uses cron syntax for scheduling jobs
• * * * * * represents execution every minute (CRON SYNTAX)
• Build periodically allows automation without manual triggers
• Execute Shell can be used for simple or complex scripts

That’s all that was required to schedule a Jenkins job at regular intervals.