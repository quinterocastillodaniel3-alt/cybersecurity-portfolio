# Windows 11 & WSL Hardening Baseline for Security Operations

## 📌 Objetivo del Proyecto
Este repositorio documenta la implementación de una línea base de fortificación (*Hardening*) y optimización de un *Endpoint* de trabajo basado en Windows 11 y el Subsistema de Windows para Linux (WSL). El propósito principal es auditar la superficie de ataque del sistema operativo anfitrión, mitigar vectores de riesgo comunes como el *ransomware* y estructurar un entorno Linux nativo de alto rendimiento para auditorías de red y despliegue de modelos de inteligencia artificial aplicados a la seguridad.

---

## 🚀 1. Optimización Avanzada del Entorno Linux (WSL)

Para evitar el sobrecosto de recursos que implican las máquinas virtuales tradicionales, se desplegó una instancia nativa de **Ubuntu** en WSL, configurando dos pilares críticos de rendimiento y auditoría:

### Aceleración por Hardware (GPU Passthrough)
Se validó la existencia del dispositivo puente de gráficos directos (`/dev/dxg`). Esto permite que el kernel de Linux acceda directamente a los núcleos de la tarjeta gráfica física. Esta configuración es vital para acelerar el procesamiento de datos masivos y el entrenamiento local de algoritmos de visión artificial y machine learning sin saturar la CPU principal.

```bash
# Verificación de la presencia de la GPU en el entorno Linux
$ ls -l /dev/dxg
crw-rw-rw- 1 root root 10, 258 Jun 13 14:29 /dev/dxg

### Mirrored Network Configuration

By default, WSL isolates the instance in a virtual subnet via NAT, which hinders communication with external hardware during infrastructure audits. To resolve this, a global directive was implemented in the Windows profile via the `.wslconfig` file:

```ini
[wsl2]
networkingMode=mirrored

Result: The Ubuntu instance shares the host machine's physical IP, enabling direct, bidirectional visibility with IoT devices, embedded systems, and traffic analysis tools on the local network.

🛡️ 2. Host System Auditing and Hardening (Windows)
Phase 1: Full Disk Encryption (FDE) Analysis
A forensic audit was performed via the command-line interface (CLI) using the manage-bde tool to verify the cryptographic encryption status of the main C: volume.

Technical Finding:
The command returned a fully decrypted conversion status (0.0% encrypted) and system error 0x8031005a, confirming a licensing limitation due to the use of a Windows Home edition, coupled with hardware restrictions regarding the support of the Modern Standby (HSTI) standard.

Figure 1: Forensic report of the C: drive showing the data protector disabled.

Figure 2: Absence of the fast encryption feature in the operating system's graphical interface.

Phase 2: Ransomware Mitigation and Access Control (Zero Trust)
As a countermeasure to the inability to activate native encryption due to license restrictions, file system security was elevated by implementing a Controlled folder access policy through the system's protection engine.

Mitigation Action:
This directive applies a Zero Trust approach over critical development directories, documents, and repositories. It strictly and instantly blocks any attempt at modification, writing, or malicious encryption originating from unauthorized processes or scripts in memory.

Figure 3: Activation of the anti-ransomware shield on the Endpoint's directories.

🛠️ Tools Used
Windows Subsystem for Linux (WSLg): Optimized base operating environment.

PowerShell (Administrator): Primary CLI for internal policy auditing.

Microsoft Windows Defender: Mitigation and controlled access engine.

Visual Studio Code: Primary editor integrated via native IPC tunnels with the Linux environment.
