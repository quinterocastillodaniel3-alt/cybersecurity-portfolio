# Windows 11 & WSL Hardening Baseline for Security Operations

## 📌 Project Objective
This repository documents the implementation of a hardening baseline and optimization of a working Endpoint based on Windows 11 and the Windows Subsystem for Linux (WSL). The primary purpose is to audit the host operating system's attack surface, mitigate common risk vectors such as ransomware, and structure a high-performance native Linux environment for network auditing and the deployment of security-applied artificial intelligence models.

---

## 🚀 1. Advanced Linux Environment Optimization (WSL)

To avoid the resource overhead of traditional virtual machines, a native **Ubuntu** instance was deployed in WSL, configuring two critical pillars for performance and auditing:

### Hardware Acceleration (GPU Passthrough)
The existence of the direct graphics bridge device (`/dev/dxg`) was validated. This allows the Linux kernel direct access to the physical graphics card cores. This configuration is vital for accelerating massive data processing and local training of computer vision and machine learning algorithms without saturating the main CPU.

```bash
# Verification of GPU presence in the Linux environment
$ ls -l /dev/dxg
crw-rw-rw- 1 root root 10, 258 Jun 13 14:29 /dev/dxg
