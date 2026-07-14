# Linux Users & Groups Administration

> This project is part of my Cloud Support Engineering portfolio and demonstrates practical Linux administration, access control, and troubleshooting skills through a real-world scenario.

> **Status:** ✅ Complete

## Project Highlights

- Linux Administration
- User & Group Management
- Linux Permissions
- Access Control
- Least Privilege
- Troubleshooting
- Technical Documentation

---

## Technologies Used

- Ubuntu 24.04 LTS (WSL2)
- Bash
- Linux User Management
- Linux Group Management
- Linux File Permissions
- `useradd`
- `usermod`
- `groupadd`
- `passwd`
- `chmod`
- `chgrp`
- Git
- GitHub

---

## Table of Contents

- [Overview](#overview)
- [Business Scenario](#business-scenario)
- [Objectives](#objectives)
- [Environment](#environment)
- [Project Structure](#project-structure)
- [Key Linux Concepts](#key-linux-concepts)
- [Implementation](#implementation)
- [Verification](#verification)
- [Skills Demonstrated](#skills-demonstrated)
- [Lessons Learned](#lessons-learned)
- [Future Improvements](#future-improvements)
- [Author](#author)

---

# Overview

This project simulates a real-world Linux administration task by implementing secure user access to a shared project directory using Linux users, groups, ownership, and permissions.

The solution follows the principle of least privilege and standard Linux filesystem practices while demonstrating how Linux administrators configure secure access for multiple users.

---

# Business Scenario

A Cloud Support Engineer is responsible for configuring a secure shared project directory for an operations team. Team members require access to shared documentation while ensuring that unauthorized users cannot view or modify sensitive project files.

The solution uses Linux users, groups, ownership, and permissions to implement least-privilege access following Linux security best practices.

---

# Objectives

During this project, I aimed to:

- Create and manage Linux users
- Create and manage Linux groups
- Configure secure shared directories
- Assign users to shared groups
- Apply Linux ownership and permissions
- Verify access using multiple user accounts
- Troubleshoot and resolve permission-related issues
- Follow Linux filesystem best practices

---

# Environment

| Component | Details |
|-----------|---------|
| Operating System | Ubuntu 24.04 LTS (WSL2) |
| Host Operating System | Windows 11 |
| Editor | Visual Studio Code |
| Shell | Bash |
| Version Control | Git |
| Repository Hosting | GitHub |

---

# Project Structure

```text
linux-users-groups-administration/
├── README.md
├── investigation-notes.md
├── documents/
└── screenshots/
```

### Directory Purpose

| Item | Purpose |
|------|---------|
| README.md | Project documentation and walkthrough |
| investigation-notes.md | Investigation notes captured during troubleshooting |
| documents/ | Supporting project files |
| screenshots/ | Screenshots used to verify implementation |

---

# Key Linux Concepts

This project demonstrates several core Linux administration concepts commonly used in enterprise environments.

| Concept | Description |
|----------|-------------|
| Users | Individual Linux accounts identified by a unique User ID (UID). |
| Groups | Collections of users used to simplify permission management. |
| Ownership | Files and directories are assigned both an owner and a group. |
| Permissions | Read, write, and execute permissions control access to resources. |
| Least Privilege | Users receive only the permissions required to perform their tasks. |
| Filesystem Hierarchy | Shared resources were relocated to `/srv` following Linux filesystem best practices. |
| Troubleshooting | Access issues were diagnosed through systematic investigation and verification. |

---

# Implementation

## Step 1 — Assess the Environment

The investigation began by identifying the current user account and reviewing existing group memberships. This established the baseline environment before making any administrative changes.

**Key commands**

```bash
whoami
id
groups
```

---

## Step 2 — Create Administrative Resources

A new Linux user (`alex`) and a shared Linux group (`cloudsupport`) were created to simulate a real-world team environment.

**Key commands**

```bash
sudo groupadd cloudsupport
sudo useradd -m alex
sudo passwd alex
```

---

## Step 3 — Configure Shared Storage

A shared project directory was created to simulate a collaborative workspace where multiple users required controlled access.

During implementation, the shared directory was initially created inside a user's home directory before being redesigned to follow Linux filesystem best practices.

**Key commands**

```bash
mkdir shared
mkdir shared/project-files
touch project-plan.txt
```

---

## Step 4 — Apply Ownership and Permissions

Group ownership was assigned to the shared directory and Linux permissions were configured following the principle of least privilege.

**Key commands**

```bash
chgrp
chmod
```

---

## Step 5 — Investigate Access Failure

Access was tested using the newly created user account (`alex`). Initial testing failed, leading to additional investigation of Linux group membership and parent directory permissions.

The shared project directory was ultimately relocated to `/srv/cloudsupport`, providing a more appropriate location for shared resources while maintaining secure access controls.

---

## Step 6 — Resolve and Verify Access

After updating group membership and relocating the shared directory, access was successfully verified using the `alex` account.

Verification confirmed that authorized users could access the shared project directory while unauthorized users remained restricted.

---

# Verification

The implementation was verified by testing access from multiple user accounts.

## Verification Checklist

| Test | Result |
|------|--------|
| Created Linux user (`alex`) | ✅ Passed |
| Created Linux group (`cloudsupport`) | ✅ Passed |
| Added user to shared group | ✅ Passed |
| Configured directory ownership | ✅ Passed |
| Configured directory permissions | ✅ Passed |
| Verified access using `alex` | ✅ Passed |
| Verified shared file access | ✅ Passed |

### Example Verification

```text
uid=1001(alex)
groups=1002(alex),1001(cloudsupport)

drwxrwx--- root cloudsupport project-files
-rw-rw---- gabby cloudsupport project-plan.txt
```

### Screenshots

The following screenshots document the implementation process.

- User creation
- Group membership verification
- Permission configuration
- Successful access verification

---

# Skills Demonstrated

## Linux Administration

- User management
- Group management
- Group membership administration
- File ownership
- File and directory permissions

## Security

- Least privilege
- Access control
- Secure shared resources
- Group-based authorization

## Troubleshooting

- User access investigation
- Permission troubleshooting
- Root cause analysis
- Verification and testing

## Professional Skills

- Technical documentation
- Problem solving
- Evidence-based troubleshooting

---

# Lessons Learned

This project reinforced several important Linux administration concepts.

- Linux access depends on both permissions and group membership.
- Shared resources should be stored in appropriate system locations such as `/srv` instead of individual user home directories.
- Directory permissions affect access to all child resources.
- Testing changes using a separate user account is essential when verifying access.
- Small configuration mistakes can often be identified by carefully reading Linux error messages before making changes.

One unexpected challenge occurred during implementation when the shared directory was initially created inside a user's home directory. Although file permissions were configured correctly, access still failed because Linux requires execute permission on every parent directory in the path.

Rather than weakening the security of the home directory, the project was redesigned to use `/srv/cloudsupport`, which better reflects Linux filesystem best practices for shared service resources.

---

# Future Improvements

Future enhancements for this project could include:

- Configure shared directory inheritance using the SetGID bit.
- Implement POSIX Access Control Lists (ACLs) for more granular permissions.
- Automate user and group provisioning with Bash scripts.
- Extend the project to an AWS EC2 Linux instance.
- Demonstrate multi-team access using role-based permission models.

---

# Author

**Gabby**

Cloud Support Engineer candidate building hands-on Linux, AWS, networking, and cloud infrastructure projects.

GitHub: https://github.com/GabbyCloudSec

---

⭐ If you have suggestions or feedback on this project, feel free to connect with me on GitHub.