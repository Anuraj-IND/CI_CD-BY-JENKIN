REMOTE SERVER COMMUNICATION USING SSH (PASSWORDLESS SETUP)

Earlier, all Jenkins work was done on a single server.
Now, to use remote server control features of Jenkins, I configured SSH communication between two systems.

System setup:
• System 1 → Source / Jenkins controller
• System 2 → Remote target server

Goal:
Allow both systems to communicate using SSH without entering password every time.

STEP 1: SSH CONNECTIVITY TEST

From System 1, I tried connecting to System 2 using SSH.

Wrong commands tried initially:
• shh → command not found
• sh → treated as a shell command

Correct command:
ssh system2@192.168.88.130

On first connection:
• SSH asked to verify host authenticity
• Typed yes to trust the host
• Entered System 2 password
• SSH connection was successful

This confirmed that SSH connectivity was working.

STEP 2: GENERATING SSH KEY PAIR (ON SYSTEM 1)

To avoid entering the password every time, I generated an SSH key pair on System 1.

Command used:
ssh-keygen

• ED25519 key pair was generated
• Private key stored in: /home/system1/.ssh/id_ed25519
• Public key stored in: /home/system1/.ssh/id_ed25519.pub

No passphrase was used.

STEP 3: COPYING PUBLIC KEY TO SYSTEM 2

To enable passwordless login, I copied the public key from System 1 to System 2.

Command used:
ssh-copy-id system2@192.168.88.130

• Entered System 2 password one last time
• Public key was added to authorized keys on System 2

STEP 4: PASSWORDLESS SSH VERIFICATION

After key setup, I tested SSH again.

Command used:
ssh system2@192.168.88.130

Result:
• Logged in successfully
• No password was asked
• Remote server access worked correctly

FINAL OUTCOME

• System 1 and System 2 can now communicate via SSH
• Password is no longer required for login
• This setup enables Jenkins to control and run jobs on remote servers

KEY LEARNINGS

• ssh is used for remote login
• First SSH connection requires host verification
• SSH key-based authentication removes password prompts
• ssh-keygen creates key pairs
• ssh-copy-id enables passwordless access
• Required for Jenkins distributed / remote builds

This setup is essential for Jenkins master–agent (controller–node) architecture and remote command execution.