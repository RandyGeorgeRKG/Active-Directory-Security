# Active-Directory (Security Focus)

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

## Group Policy Implementation(Account Lockout and Password Complexity) 
In this section of my project, I implemented Group Policy for my domain on the Windows 10 machine within my network. I accomplished this using the Group Policy Management Editor. First, I configured the Account Lockout Policy with the following settings:

Lockout Duration: 30 minutes
Account Lockout Threshold: 4 invalid logon attempts
Reset Account Lockout Counter After: 30 minutes
This lockout policy is designed to reduce the risk of a successful brute-force attack by limiting the number of login attempts.

Next, I adjusted the Password Policy to enforce stronger password practices:

Enforce Password History: 24 passwords
Maximum Password Age: 100 days
Minimum Password Age: 30 days
Minimum Password Length: 14 characters
These settings are intended to ensure the use of complex passwords, making it more difficult for attackers to crack weak passwords.

Following these changes, I used the Remote Group Policy Update rule to push the updated policies to my Windows 10 VM. On the Windows 10 machine, I ran the gpupdate /force command to apply the new group policies immediately. To verify the effectiveness of the password policy, I tested it by entering a weak password, and the policy successfully prevented its use.

Implementing these group policies is crucial for hardening the Active Directory environment and reducing the attack surface within an organization.


![More account lockouts ](https://github.com/user-attachments/assets/b8a6a520-ecc2-42e4-b75b-644aac4f787e)![More Password GPO ](https://github.com/user-attachments/assets/b2bcc5a6-48d8-4d9a-9f60-2496432ee276)
![PAssword Policy GPO ](https://github.com/user-attachments/assets/cc5257a6-a507-4b8e-8a61-88730e195df5)
![Account Lockouts ](https://github.com/user-attachments/assets/c29258a3-296d-47dd-ae1d-2b9509a5f4e8)
![Pushed GPO to the machine ](https://github.com/user-attachments/assets/54cc07d0-20f2-43ce-a690-4b9199088b0c)

##  Identity Acess Management(IAM) RBAC 
In this section, I focused on practicing Identity and Access Management (IAM) for my Domain Controller in Active Directory. To do this, I created an automation script to add over 1,000 users via the command prompt. While manually adding users one by one is possible, automating the process provides a more efficient solution, especially when handling large volumes of users.
![Screenshot 2024-11-26 102222](https://github.com/user-attachments/assets/19bbcea1-4005-4f65-b793-8f964c1d253d)

After creating the users, I proceeded to create groups to assign specific rights and privileges, thereby enforcing Role-Based Access Control (RBAC). I included my own user account in the script and created a group called "Admins Group for RBAC Project." Several other users were also added to this group to facilitate the IAM practice. I then used the Delegation Control Wizard to assign tasks such as creating, deleting, and managing user accounts and groups.

This delegation ensures that users within this group have the necessary permissions to perform these tasks, while users outside the group are restricted from doing so. This approach aligns with the principle of least privilege, which dictates that users should only be granted the permissions required to complete their specific duties. Granting excessive permissions could pose significant security risks and increase the vulnerability of the organization to cyber threats.

![RBAC Controls ](https://github.com/user-attachments/assets/a4c4e84c-0201-45cc-bb69-877c047ba393)
![Screenshot 2024-11-26 215645](https://github.com/user-attachments/assets/fb5d2b1b-018c-4793-89f2-357155092ca3)

Once the rights were delegated to the group, I accessed the Computer Management tool on my machine and navigated to the Remote Desktop Users group. I added the "Admins Group for RBAC Project" to this group, which ensures that the roles and privileges are inherited through Active Directory. To verify the setup, I tested my ability to remotely log into the system, which was successful.

This project provided valuable hands-on experience with IAM and RBAC, deepening my understanding of how roles, permissions, and security principles are effectively managed within Active Directory.


![Screenshot 2024-11-26 220135](https://github.com/user-attachments/assets/dcc579b6-6bac-45ca-8af9-908a4e955102)


##  Monitoring and Auditing Logs

In this section of the project, my goal was to increase the volume and visibility of logs generated by the Domain Controller. Logs are one of the most critical tools IT professionals rely on for day-to-day operations. They provide visibility into the actions occurring within an environment, offering invaluable insights that enhance security and operational awareness. Without adequate logging, visibility is significantly reduced, increasing the organization's risk and exposure to potential vulnerabilities.

To achieve this, I used the Group Policy Management tool. I navigated to Group Policy Objects (GPO) within RKGInfosec.Local (my domain), where I created a new GPO titled Audit Policies for RBAC Project.

From there, I proceeded to:

Navigate to Computer Configuration and expand to Audit Policies.
Configure the following settings to monitor and capture critical events:
Audit Logon/Logoff Events: Enabled logging for both successful and failed logon attempts, which is crucial for detecting unauthorized access or potential cybersecurity incidents.
Audit Account Lockout: Monitored both success and failure events to track any account lockout incidents, which may indicate brute-force attacks or misconfigurations.
Audit Credential Validation: Enabled success and failure events to track credential validation activities, ensuring visibility into potential authentication anomalies.
Once the policy was configured, I returned to the Group Policy Management console, moved the audit GPO to the top of my domain hierarchy, and enforced it across the domain to ensure it applied to all relevant systems, including my Windows 10 virtual machine.

To expedite the policy application, I logged into the Windows 10 machine and executed the gpupdate /force command. This ensured the GPO was inherited promptly.

Finally, I validated the implementation by testing the configurations and observing the Event Viewer on the Windows 10 machine. The expected events and incidents were successfully logged, confirming that the audit policies were functioning as intended.

Monitoring and auditing logs within an Active Directory environment is essential for detecting both external threats and potential insider risks. By leveraging these logs, IT professionals can proactively monitor, investigate, and respond to security incidents, thereby enhancing the overall security posture of the environment.
![Screenshot 2024-11-26 225359](https://github.com/user-attachments/assets/94906a84-3506-4491-b6c2-ecc0f92c5898)![Screenshot 2024-11-26 225600](https://github.com/user-attachments/assets/75361a6e-efe3-4bc4-9af6-394040966c50)
![Screenshot 2024-11-26 225618](https://github.com/user-attachments/assets/d6b44944-180c-4234-ac0b-e8150fa62a36)![Screenshot 2024-11-26 225658](https://github.com/user-attachments/assets/017b484f-6ab8-42ce-932b-f16a7033f3a5)


![Screenshot 2024-11-26 225933](https://github.com/user-attachments/assets/06895a8f-61a6-4bc2-9265-b1428f19d2bb)



##  Security Hardening
In this section of the project, I focused on security hardening for the Domain Controller. I began by generating random users and assigning them to specific privileged groups, applying the principle of least privilege. Through Group Policy, I modified permissions to restrict remote desktop access, deny local logins, and block logon as a service, logon as a batch job, and network access from specific computers.

I then reviewed the membership of high-privilege groups, specifically the Enterprise Admins and Domain Admins groups. I found several users who did not require such elevated privileges, so I removed them from these groups. This ensured that only trusted administrators retained these high-level permissions within Active Directory.

Security hardening is a critical process to minimize the attack surface and enhance the protection of the Domain Controller, helping to safeguard the entire network.


![Screenshot 2024-11-27 115952](https://github.com/user-attachments/assets/945e2dc7-59d8-424f-ae5c-d922a4e125ab)
![Screenshot 2024-11-27 115747](https://github.com/user-attachments/assets/e8b6af6d-f957-4ae3-be1d-415a864f7d14)
![Screenshot 2024-11-27 115412](https://github.com/user-attachments/assets/862b48d0-96a2-4529-9991-fb019122863f)
![Screenshot 2024-11-27 115349](https://github.com/user-attachments/assets/482d1e8b-59ea-4d06-9e60-950515ffb3b7)
![Screenshot 2024-11-27 115329](https://github.com/user-attachments/assets/d84721ad-87fe-4861-a20e-6606685eea69)
![Screenshot 2024-11-27 115229](https://github.com/user-attachments/assets/f645f544-321c-4a54-8c35-280cf9c889a3)













