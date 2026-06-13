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
