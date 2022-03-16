Domain: Network Security

# Question 1: Faulty Firewall

Suppose you have a firewall that's supposed to block SSH connections, but instead lets them through. How would you debug it?
Make sure each section of your response answers the questions laid out below. ​

Restate the Problem


## Provide a Concrete Example Scenario

### In Project 1, did you allow SSH traffic to all of the VMs on your network?

No. 

### Which VMs did accept SSH connections?

- Jumpbox from Public
- Webserver from Ansible Container on Jumpbox
- Elk Server from Ansible Container on Jumpbox

### What happens if you try to connect to a VM that does not accept SSH connections? Why?

You are either dropped or timed out, due to either Firewall/Security Group denying SSH access.

## Explain the Solution Requirements

### If one of your Project 1 VMs accepted SSH connections, what would you assume the source of the error is?

Our Firewall/Security Group configured incorrectly and allowing possibly all IPs from the public to access.

### Which general configurations would you double-check?

Security Group Rules for SSH

### What actions would you take to test that your new configurations are effective?

Attempt to SSH into the Endpoint being tested

## Explain the Solution Details

### Which specific panes in the Azure UI would you look at to investigate the pr oblem?

Network Security Groups

### Which specific configurations and controls would you check?

Would check either RedTeamSG or ElkNetSG and check the Inbound Security Group Rules for SSH

### What would you look for, specifically?

Rules that allow port 22 access, specifically the source.

### How would you attempt to connect to your VMs to test that your fix is effective?

SSH into the endpoint through terminal/CMD

## Identify Advantages/Disadvantages of the Solution

### Does your solution guarantee that the Project 1 network is now "immune" to all unauthorized access?

No

### What monitoring controls might you add to ensure that you identify any suspicious authentication attempts?​

Account Lockout Policies, Authentication Attempts Logging


