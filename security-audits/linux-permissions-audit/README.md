# Linux File Permissions Management - Security Audit

## 📌 Project Description
As a security professional in a large organization, part of my role involves ensuring that users within the research team have the appropriate authorizations to maintain system security. In this project, I performed a security audit of a Linux file system. The objective was to examine existing permissions, identify misconfigurations, and apply the **Principle of Least Privilege** by modifying permissions to remove unauthorized access and secure sensitive research files.

---

## 🔍 Checking File and Directory Details
To begin the investigation, I needed to check the current permissions set for the files and subdirectories within the `projects` directory. It was crucial to display all files, including hidden ones.

**Command used:**
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

---

## 📖 Describing the Permissions String
In Linux, file permissions are represented by a 10-character string. Taking the file `project_m.txt` (`-rw-rw-rw-`) as an example, here is the breakdown of what each character represents:

* **1st Character (`-`)**: Represents the file type. A hyphen (`-`) indicates a regular file, while a `d` would indicate a directory.
* **2nd, 3rd, 4th Characters (`rw-`)**: Represent the **Owner (User)** permissions. `r` means read, `w` means write, and `-` means execute is not allowed.
* **5th, 6th, 7th Characters (`rw-`)**: Represent the **Group** permissions. Anyone in the assigned group can read and write.
* **8th, 9th, 10th Characters (`rw-`)**: Represent the **Others** permissions. This means any other user on the system has read and write access, which is a significant security risk.

---

## 🛡️ Changing File Permissions
The organization's security policy strictly states that "Other" users should not have write access to any files. Based on the previous output, `project_m.txt` had unauthorized write permissions for others (`-rw-rw-rw-`).

To revoke the write access for others without affecting the owner or group, I used the following command:

**Command used:**
```bash
chmod o-w project_m.txt
```
*Result: The permissions string for `project_m.txt` was successfully updated to `-rw-rw-r--`, securing it against unauthorized modifications.*

---

## 🔒 Changing File Permissions on a Hidden File
The research team archived a log file named `.project_x.txt`. As a hidden file, it requires strict access controls. It should not have write permissions for anyone, but both the user (owner) and the group should retain read access.

To assign the appropriate authorization, I used absolute (octal) mode:

**Command used:**
```bash
chmod 440 .project_x.txt
```
*Result: This command changed the permissions to `-r--r-----`. Now, the owner and group can read the file (4), but no one has write or execute permissions, and 'others' have absolutely no access (0).*

---

## 📁 Changing Directory Permissions
The `drafts` directory and its contents belong exclusively to the user `researcher2`. To prevent unauthorized access, lateral movement, or data leaks, only `researcher2` should be allowed to access this directory.

To lock down the directory completely, I used the following command:

**Command used:**
```bash
chmod 700 drafts
```
*Result: The permissions for the `drafts` directory were updated to `drwx------`. This ensures that only the owner has full read, write, and execute (traverse) rights, completely blocking out the group and other users.*

---

## 📝 Summary
In this scenario, I successfully audited and hardened a Linux file system for a research team. By utilizing core Linux commands like `ls -la` to inspect ownership and `chmod` to modify access rights, I mitigated security risks associated with overly permissive settings. I revoked public write access to collaborative files, secured hidden archives to a read-only state for authorized personnel, and isolated sensitive directories. This exercise demonstrates my ability to navigate the Linux command line and practically apply access control concepts to protect organizational data.
