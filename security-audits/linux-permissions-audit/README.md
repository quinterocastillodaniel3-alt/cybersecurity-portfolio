# Linux File Permissions Management & Security Audit

[![Linux Security](https://img.shields.io/badge/OS-Linux_Security-blue?style=for-the-badge)](https://www.kernel.org/doc/html/latest/security/index.html)
[![IAM](https://img.shields.io/badge/Domain-Identity_%26_Access_Management-darkgreen?style=for-the-badge)](https://en.wikipedia.org/wiki/Identity_and_access_management)
[![Least Privilege](https://img.shields.io/badge/Security_Principle-Least_Privilege-red?style=for-the-badge)](https://www.cisa.gov/uscert/bsi/articles/knowledge/principles/least-privilege)

## 📌 Project Description
As a security professional, part of my role involves auditing user authorizations to maintain robust system security. In this project, I performed a security audit of a Linux file system utilized by a corporate research team. 

The objective was to examine existing access controls, identify misconfigurations, and strictly enforce the **Principle of Least Privilege (PoLP)** by modifying permissions to revoke unauthorized access, thereby securing sensitive research files and directories.

---

## 🔍 Phase 1: File System Baseline & Triage
To begin the investigation, I needed to establish a baseline of the current permissions set for the files and subdirectories within the `projects` directory. It was crucial to display all contents, including hidden system or archive files.

**Command Executed:**
```bash
ls -la
```

**Output:**
```text
drwxr-xr-x 3 researcher2 research 4096 Jun 29 09:00 .
drwxr-xr-x 4 root        root     4096 Jun 29 08:45 ..
-rw-r----- 1 researcher2 research  240 Jun 29 08:50 .project_x.txt
-rw-rw-rw- 1 researcher2 research 1024 Jun 29 08:52 project_m.txt
drwxr-xr-x 2 researcher2 research 4096 Jun 29 08:55 drafts
```

### 📖 Permissions String Breakdown
In Linux, file permissions are represented by a 10-character string. Taking the heavily misconfigured file `project_m.txt` (`-rw-rw-rw-`) as an example, the breakdown is as follows:
* **1st Character (`-`)**: Represents the file type (hyphen = regular file, `d` = directory).
* **2nd, 3rd, 4th (`rw-`)**: **Owner (User)** permissions. Read (`r`), Write (`w`), and Execute (`x`).
* **5th, 6th, 7th (`rw-`)**: **Group** permissions. Users in the `research` group can read and write.
* **8th, 9th, 10th (`rw-`)**: **Others** permissions. Any other authenticated user on the system has read and write access, representing a critical security risk (Data Modification).

---

## 🛡️ Phase 2: Remediation & Access Control Updates

### Remediation 1: Revoking Global Write Access (Symbolic Mode)
The organization's security policy strictly dictates that "Other" users must not have write access to collaborative files. Based on the baseline output, `project_m.txt` possessed unauthorized global write permissions (`-rw-rw-rw-`).

To revoke the write access for others without disrupting the owner or group workflows, I utilized symbolic modification:

**Command Executed:**
```bash
chmod o-w project_m.txt
```
* **Result:** The permissions string for `project_m.txt` was successfully hardened to `-rw-rw-r--`, securing it against unauthorized modifications while allowing public read access.

### Remediation 2: Securing Hidden Archives (Absolute/Octal Mode)
The research team archived a log file named `.project_x.txt`. As a hidden archive, it requires strict access controls. It must not have write permissions for anyone, but both the user (owner) and the group must retain read access.

To assign this exact authorization efficiently, I utilized absolute (octal) mode:

**Command Executed:**
```bash
chmod 440 .project_x.txt
```
* **Result:** The permissions were updated to `-r--r-----`. The owner and group can read the file (4+0=4), but 'others' have absolutely no access (0).

### Remediation 3: Directory Isolation (Zero Trust)
The `drafts` directory and its contents belong exclusively to the user `researcher2`. To prevent unauthorized access, lateral movement, or internal data leaks, only `researcher2` should be permitted to traverse this directory.

To lock down the directory completely, I enforced strict isolation:

**Command Executed:**
```bash
chmod 700 drafts
```
* **Result:** The permissions for the `drafts` directory were updated to `drwx------`. This ensures that only the owner has full read, write, and execute (traverse) rights, completely blocking out the group and all other users.

---

## 📝 Summary & Security Impact
In this scenario, I successfully audited and hardened a Linux file system. By utilizing core Linux utilities (`ls -la` to inspect ownership/permissions and `chmod` to modify access rights), I mitigated the security risks associated with overly permissive (Access Drift) settings. 

I revoked public write access to collaborative files, secured hidden archives to a read-only state, and isolated sensitive user directories. This exercise demonstrates a practical application of the Principle of Least Privilege and the ability to navigate the Linux command line to enforce organizational data protection policies.
