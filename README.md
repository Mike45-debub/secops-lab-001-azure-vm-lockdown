# secops-lab-001-azure-vm-lockdown
Deployed and secured a Linux VM on Azure. Implemented manual SSH lockdown using NSG rules as Just-In-Time access alternative.
SecOps Lab 001 – SSH Lockdown on Azure Linux VM
Objective
This lab was focused on deploying a Linux virtual machine in Azure using free-tier resources and securing access by manually controlling SSH availability. Since the Just-In-Time access feature wasn't supported for the VM I used, I simulated that behavior by managing the Network Security Group (NSG) rules directly.

Azure Setup
Created a resource group named SecLab-RG
Deployed an Ubuntu Server 24.04 LTS VM using the B1ls size (free-tier eligible)
Enabled auto-shutdown to prevent accidental charges
Allowed SSH (port 22) temporarily during setup
After accessing the VM, I deleted the NSG rule that allowed SSH to simulate a Just-In-Time access control scenario

Local Machine Actions (Windows)
Used Windows Command Prompt to connect via SSH:
ssh secadmin@98.71.32.31
Successfully logged into the VM and confirmed it was running as expected
Logged out of the session using the exit command
Attempted to reconnect and received a timeout error, confirming that the NSG rule had successfully blocked SSH access
Cmd information Below

C:\Users\m_pow>ssh secadmin@98.71.32.31
secadmin@98.71.32.31's password:
Welcome to Ubuntu 24.04.2 LTS (GNU/Linux 6.11.0-1015-azure x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/pro

 System information as of Fri May 30 22:32:34 UTC 2025

  System load:  0.0               Processes:             109
  Usage of /:   5.5% of 28.02GB   Users logged in:       0
  Memory usage: 68%               IPv4 address for eth0: 10.0.0.4
  Swap usage:   0%
secadmin@SecLabVM:~$ exit
logout
Connection to 98.71.32.31 closed.

C:\Users\m_pow>ssh secadmin@98.71.32.31
ssh: connect to host 98.71.32.31 port 22: Connection timed out
