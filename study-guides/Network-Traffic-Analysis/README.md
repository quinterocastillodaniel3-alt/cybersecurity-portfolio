# 🌐 Análisis de Tráfico y Seguridad de Red

Repositorio dedicado a la comprensión del tráfico de red, inspección de paquetes y detección de anomalías utilizando herramientas de línea de comandos.

---

## 📡 Fundamentos del Tráfico de Red

Monitorizar y comprender el tráfico es vital en ciberseguridad porque:
1. Ayuda a identificar desviaciones respecto a los flujos de tráfico previstos (establecimiento de líneas base).
2. Ayuda a detectar intrusiones y detectar tácticas como el **movimiento lateral** (cuando un atacante amplía su acceso no autorizado saltando de un equipo a otro dentro de la misma red).

### Modelo TCP/IP y Empaquetado
* **Capa de Acceso a la Red:** Es la capa inferior del modelo TCP/IP, responsable directa de aceptar y entregar físicamente los paquetes en una red (ya sea por cable de cobre, fibra óptica o Wi-Fi).
* **Anatomía del Encabezado IPv4:** Un paquete de red es como una carta; el encabezado es el "sobre" y contiene información de enrutamiento crucial:
  * **Direcciones IP:** Identifican el origen y el destino.
  * **Protocolos:** Utiliza un valor numérico para representar un estándar específico (ej. el número 6 representa a TCP y el 17 a UDP).
  * **Puertos:** Indican la aplicación o servicio lógico de destino.
  * **Tiempo de Vivir (TTL):** Campo que determina cuánto tiempo (número de saltos por routers) puede viajar un paquete antes de ser descartado para evitar bucles infinitos.
  * *Nota de seguridad:* Los datos de la **carga útil** (Payload), que es el mensaje real, **no** forman parte del encabezado.

---

## 🛠️ Captura y Análisis de Paquetes

Los archivos de captura de paquetes (comúnmente con extensión `.pcap`) proporcionan instantáneas detalladas e íntegras de las comunicaciones de red que fueron interceptadas desde una interfaz. 

Las herramientas del analizador de protocolos de red están disponibles para ser utilizadas en dos modalidades principales:
* **Interfaz Gráfica de Usuario (GUI):** Como Wireshark.
* **Interfaz de Línea de Comandos (CLI):** Como `tcpdump` o `tshark`.

### Uso de tcpdump
Para obtener una salida con información detallada sobre paquetes escuchando en todas las interfaces, el comando con la sintaxis correcta en Linux es:

```bash
sudo tcpdump -i any -v
```
*(Nota: La bandera `-i` siempre debe ir seguida de la interfaz, en este caso `any`, y `-v` activa el modo verbose/detallado).*

**Lectura de registros de tcpdump:**
Al examinar la siguiente salida:
```text
22:00:19.538395 IP 198.168.105.1.41012 > 198.111.123.1.61012: Flags [P.]
```
La dirección IP de origen es **198.168.105.1**. En la nomenclatura estándar, la estructura siempre muestra el `Origen > Destino`, separando la IP del puerto con un punto.

---

## 🐍 Extra: Automatización Básica con Python y Scapy

Para el análisis masivo de archivos de captura, los analistas de seguridad suelen crear scripts. A continuación, un ejemplo básico utilizando la librería `Scapy` de Python para extraer y listar las direcciones IP de origen y destino de un archivo `.pcap`:

```python
from scapy.all import rdpcap, IP

def analizar_pcap(archivo):
    # Cargar el archivo de captura de red
    paquetes = rdpcap(archivo)
    
    print(f"Analizando: {archivo}\n{'-'*30}")
    
    # Iterar sobre los paquetes e imprimir Origen -> Destino
    for paquete in paquetes:
        if IP in paquete:
            ip_origen = paquete[IP].src
            ip_destino = paquete[IP].dst
            print(f"Tráfico detectado: {ip_origen} -> {ip_destino}")

# Ejemplo de uso:
# analizar_pcap("captura_incidente.pcap")
```
