# Active-Directory-Security

![Microsoft-Active-Directory-Integration-1440x960](https://github.com/user-attachments/assets/d493fd90-1d39-4e22-9d6b-7ec2151273f7)

## Introduction
Howdy!

Thank you for taking the time to review my Active Directory project. Active Directory was one of the first IT tools I mastered during my role as an IT Manager for a department. Recognizing its significance, I quickly realized that Active Directory is widely used across various industries. This inspired me to take the initiative to build a basic development environment at home to deepen my understanding of how it can be effectively utilized in a production environment.

There are several key security benefits of transitioning your environment to Active Directory, including:

Enforcement of Role-Based Access Control (RBAC), Centralized Auditing and Monitoring, Kerberos Authentication, Centralized User Account Management and etc. 

Many organizations are adopting Active Directory to enhance their security posture and address the ever-evolving threat landscape. In my experience, it is one of the most effective tools available to safeguard an organization’s data and infrastructure.

Thank you again for your interest, and I look forward to your feedback!


## Project Overview
In this project, my objective was to build a solid foundational understanding of Active Directory (AD) in a virtualized environment. I used VMware to set up a virtualization host, which included:

A Domain Controller (DC) running Windows Server 2022
A Windows 10 virtual machine (VM)
Network Configuration
I configured the Domain Controller with two Network Interface Cards (NICs):

NIC 1 (External): Connected to the public internet
NIC 2 (Internal): Connected to a private internal network
The Windows 10 VM was configured with a NIC connected to the internal network, allowing it to communicate with the Domain Controller. This setup created a NAT (Network Address Translation) environment, enabling the Windows 10 VM to access external internet resources through the Domain Controller.

DHCP Configuration
On the Domain Controller, I configured DHCP to dynamically assign IP addresses to devices within the domain. This ensured that domain-joined machines automatically received a leased IP address upon reboot, streamlining network management.

Automation and Role-Based Access Control (RBAC)
To practice automation, I used PowerShell to create 100 user accounts in Active Directory. This allowed me to simulate a large user base and implement Role-Based Access Control (RBAC), a critical component of Identity and Access Management (IAM). By assigning roles and permissions to these users, I was able to enforce the principle of least privilege across the domain.

Group Policy Implementation
I implemented Group Policy Objects (GPOs) to enforce security policies across the environment. These policies included:

Password complexity requirements
Account lockout policies
Software installation restrictions
User access controls
GPOs are essential for standardizing security configurations across all domain-joined devices and ensuring compliance with organizational policies.

Monitoring, Auditing, and Security Hardening
I also focused on log management by configuring auditing policies on the Domain Controller to capture key security events, such as:

User logon and logoff events
Privilege escalation attempts
Group membership changes
These logs were monitored to highlight the importance of centralized logging for detecting potential security incidents and ensuring regulatory compliance.

Finally, I practiced security hardening techniques to reduce the attack surface of both the Domain Controller and client machines. This included:

Disabling unnecessary services and protocols
Enforcing network-level authentication
Applying the latest security patches and updates

![BLUEEEEE](https://github.com/user-attachments/assets/cfa1d79b-d14c-4ec5-bad5-e9aae9b00ae4)


##  Domain Controller Setup

![Domain Controller  blacked out intenret ](https://github.com/user-attachments/assets/d6f2be8e-9728-47b2-bd22-22fd44d870d4)



## Group Policy Implementation

##  Role-Based Access Control (RBAC)

##  Monitoring and Auditing Logs

##  Security Hardening
