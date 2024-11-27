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

![BLUEEEEE](https://github.com/user-attachments/assets/cfa1d79b-d14c-4ec5-bad5-e9aae9b00ae4)
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




##  Domain Controller Setup

![Domain Controller  blacked out intenret ](https://github.com/user-attachments/assets/d6f2be8e-9728-47b2-bd22-22fd44d870d4)

In this section of the project, I used a Windows Server 2022 ISO with VMware to set up a virtual server. Once the server was configured and accessible, I installed Active Directory (AD) via Server Manager and created a domain named RKGINFOSec (RKG stands for Randy Kurt George).
One of the key benefits of setting up a Domain Controller (DC) is its role as a centralized authentication and authorization service. It manages user, device, and service authentication across the network, eliminating the need for local authentication on individual machines. This centralized approach helps reduce the risk of weak or inconsistent credentials across the environment.

Additionally, the DC uses secure authentication protocols like Kerberos, which provides efficient and encrypted authentication, significantly enhancing security. 
The Domain Controller also enforces Group Policy Objects (GPOs) across all domain-joined machines. These policies can include:
Account lockout thresholds to prevent brute-force attacks. Password complexity requirements to ensure stronger credentials.

By standardizing security policies across the domain, GPOs help maintain consistent security configurations, reducing potential vulnerabilities.
I also implemented Role-Based Access Control (RBAC) to enforce the principle of least privilege (PoLP). This principle is critical in cybersecurity, as users should only be granted the minimum level of access necessary to perform their daily tasks. This minimizes the risk of unauthorized access, privilege escalation, or accidental data exposure, thereby reducing the overall security risk in the environment.

Active Directory is a powerful tool in today’s evolving threat landscape. Its ability to centralize authentication, enforce security policies, and manage access control makes it an essential component for safeguarding enterprise networks against internal and external threats

## Group Policy Implementation



![More account lockouts ](https://github.com/user-attachments/assets/b8a6a520-ecc2-42e4-b75b-644aac4f787e)![More Password GPO ](https://github.com/user-attachments/assets/b2bcc5a6-48d8-4d9a-9f60-2496432ee276)
![PAssword Policy GPO ](https://github.com/user-attachments/assets/cc5257a6-a507-4b8e-8a61-88730e195df5)
![Account Lockouts ](https://github.com/user-attachments/assets/c29258a3-296d-47dd-ae1d-2b9509a5f4e8)
![Pushed GPO to the machine ](https://github.com/user-attachments/assets/54cc07d0-20f2-43ce-a690-4b9199088b0c)

##  Role-Based Access Control (RBAC)

##  Monitoring and Auditing Logs

##  Security Hardening
