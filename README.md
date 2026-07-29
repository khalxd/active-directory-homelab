# Active Directory Homelab in Microsoft Azure

## Overview

This project demonstrates the deployment and configuration of an enterprise-style Active Directory environment in Microsoft Azure. The lab was built to gain hands-on experience with Windows Server administration, Identity & Access Management (IAM), DNS, Organizational Units (OUs), Security Groups, Role-Based Access Control (RBAC), and Group Policy Objects (GPOs).

The environment simulates a small corporate network consisting of a Domain Controller and a domain-joined workstation to practice common identity administration tasks.

---

# Lab Architecture

```
Microsoft Azure
│
├── Resource Group: HOMELAB
│
├── DC01
│   ├── Windows Server 2022
│   ├── Active Directory Domain Services (AD DS)
│   ├── DNS Server
│   └── homelab.local
│
└── CLIENT01
    ├── Windows Server 2022
    └── Joined to homelab.local
```

---

# Technologies Used

- Microsoft Azure
- Windows Server 2022
- Active Directory Domain Services (AD DS)
- DNS Server
- Group Policy Management
- Remote Desktop (RDP)
- Windows Command Prompt

---

# Project Objectives

- Deploy an Active Directory environment in Microsoft Azure
- Configure Active Directory Domain Services (AD DS)
- Configure DNS
- Join a workstation to the domain
- Create Organizational Units (OUs)
- Create users and security groups
- Implement Role-Based Access Control (RBAC)
- Configure and troubleshoot Group Policy Objects (GPOs)

---

# Azure Infrastructure

### Resource Group

![Resource Group](screenshots/resourcegroup.png)

### Virtual Machines

![Virtual Machines](screenshots/virtualmachines.png)

The Azure environment consists of one Domain Controller (DC01) and one domain-joined workstation (CLIENT01).

---

# Active Directory Deployment

### Active Directory Users and Computers

![Active Directory](screenshots/AD%20User%26Computers.png)

Installed and configured:

- Active Directory Domain Services
- DNS Server

Created the Active Directory domain:

```
homelab.local
```

---

# Organizational Units

![Organizational Units](screenshots/Organizational%20Units.png)

Created Organizational Units to organize resources similarly to a production environment.

Organizational Units created:

- Employees
- Workstations
- Groups
- Servers
- Service Accounts

---

# Domain Join

![Domain Joined Computer](screenshots/Domain%20Joined%20Computer.png)

Successfully joined CLIENT01 to the `homelab.local` domain and verified domain authentication.

---

# Security Groups

![Security Groups](screenshots/Group%20Membership.png)

Created security groups and assigned users following Role-Based Access Control (RBAC) principles.

Implemented:

- Security Groups
- Group Membership
- Principle of Least Privilege

---

# Group Policy Management

### Group Policy Management Console

![Group Policy Management](screenshots/Group%20Policy%20Management.png)

Created and linked a User Configuration Group Policy Object to the Employees Organizational Unit.

### Group Policy Editor

![Group Policy Editor](screenshots/Group%20Policy%20Editor.png)

Configured the following policy:

```
User Configuration
→ Policies
→ Administrative Templates
→ Control Panel
→ Prohibit access to Control Panel and PC settings
```

---

# Policy Verification

### gpresult

![gpresult](screenshots/gpresult.png)

Verified successful Group Policy application using:

```cmd
gpresult /r
```

Confirmed the policy was successfully applied to the user.

---

# Final Result

![Final Result](screenshots/FinalResult.png)

Successfully prevented users from accessing the Windows Control Panel using Group Policy.

---

# Troubleshooting

One of the most valuable parts of this project involved troubleshooting a Group Policy issue.

Initially, the User Configuration policy did not apply because the user account was located inside the default **Users** container rather than an Organizational Unit.

After investigating with:

- `gpupdate /force`
- `gpresult /r`
- Group Policy Management
- Active Directory Users and Computers

I identified that User Configuration policies follow the user's Organizational Unit. After moving the user into the **Employees** OU and linking the Group Policy correctly, the policy applied successfully.

This reinforced the importance of understanding how Active Directory processes User Configuration versus Computer Configuration policies.

---

# Skills Demonstrated

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

# Key Takeaways

Through this project I gained hands-on experience with Active Directory administration by deploying and managing a Windows domain in Microsoft Azure. I learned how DNS, Organizational Units, Security Groups, Group Policy, and authentication work together in an enterprise environment. Troubleshooting the Group Policy issue strengthened my understanding of how Windows processes user and computer policies and reinforced a structured approach to diagnosing configuration issues.

---

# Future Improvements

- Configure Password Policies
- Implement Account Lockout Policies
- Deploy File Shares and NTFS Permissions
- Configure Folder Redirection
- Configure Roaming Profiles
- Integrate Microsoft Entra ID
- Build a Hybrid Identity Environment
- Automate administration tasks with PowerShell
