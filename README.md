# Active Directory Homelab in Microsoft Azure

## Overview

This project demonstrates the deployment and configuration of an enterprise-style Active Directory environment in Microsoft Azure. The lab was built to develop hands-on experience with Windows Server administration, Identity & Access Management (IAM), DNS, Organizational Units (OUs), Security Groups, Role-Based Access Control (RBAC), and Group Policy.

The environment simulates a small corporate network consisting of a Domain Controller and a domain-joined workstation.

---

## Lab Architecture

```
Microsoft Azure
│
├── Resource Group: HOMELAB
│
├── DC01
│   ├── Windows Server 2022
│   ├── Active Directory Domain Services
│   ├── DNS Server
│   └── homelab.local
│
└── CLIENT01
    ├── Windows Server 2022
    └── Joined to homelab.local
```

---

## Objectives

- Deploy an Active Directory environment in Microsoft Azure
- Configure Active Directory Domain Services (AD DS)
- Configure DNS for domain services
- Join a workstation to the domain
- Create Organizational Units (OUs)
- Create users and security groups
- Implement Role-Based Access Control (RBAC)
- Configure and troubleshoot Group Policy Objects (GPOs)

---

## Technologies Used

- Microsoft Azure
- Windows Server 2022
- Active Directory Domain Services (AD DS)
- DNS
- Group Policy Management
- Remote Desktop (RDP)
- Windows Command Prompt

---

## Project Tasks

- Deployed a Windows Server Domain Controller (DC01)
- Installed Active Directory Domain Services
- Configured DNS
- Created the `homelab.local` domain
- Joined CLIENT01 to the domain
- Created Organizational Units for users, computers, servers, and service accounts
- Created domain users and security groups
- Added users to security groups
- Implemented Role-Based Access Control (RBAC)
- Created and linked Group Policy Objects
- Applied and verified user policies using `gpupdate` and `gpresult`

---

## Troubleshooting

One of the most valuable parts of this project involved troubleshooting a Group Policy issue.

Initially, the User Configuration policy did not apply because the user account was located inside the default **Users** container rather than an Organizational Unit. After moving the user into the **Employees** OU and linking the Group Policy correctly, the policy applied successfully.

This reinforced the importance of understanding how Active Directory processes User Configuration and Computer Configuration policies.

---

## Skills Demonstrated

- Active Directory Administration
- Windows Server Administration
- Identity & Access Management (IAM)
- DNS Administration
- Organizational Unit Design
- Security Groups
- Role-Based Access Control (RBAC)
- Group Policy Management
- Group Policy Troubleshooting
- Windows Authentication
- Azure Virtual Machines

---

## Lessons Learned

Through this project I learned how Active Directory components work together, including DNS, authentication, Organizational Units, Security Groups, and Group Policy. Troubleshooting the Group Policy issue improved my understanding of how Windows processes User Configuration versus Computer Configuration policies in enterprise environments.

---

## Future Improvements

- Implement Password Policies
- Configure Account Lockout Policies
- Deploy File Shares and NTFS Permissions
- Configure Roaming Profiles
- Integrate Microsoft Entra ID
- Build a Hybrid Identity Environment
