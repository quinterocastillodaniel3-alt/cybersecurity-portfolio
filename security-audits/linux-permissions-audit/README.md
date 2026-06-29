# Linux File Permissions Management - Security Audit

## 📌 Project Description
As a security professional in a large organization, part of my role involves ensuring that users within the research team have the appropriate authorizations to maintain system security. In this project, I performed a security audit of a Linux file system. The objective was to examine existing permissions, identify misconfigurations, and apply the **Principio del Menor Privilegio (Principle of Least Privilege)** by modifying permissions to remove unauthorized access and secure sensitive research files.

---

## 🔍 Checking File and Directory Details
To begin the investigation, I needed to check the current permissions set for the files and subdirectories within the `projects` directory. It was crucial to display all files, including hidden ones.

**Command used:**
```bash
ls -la
