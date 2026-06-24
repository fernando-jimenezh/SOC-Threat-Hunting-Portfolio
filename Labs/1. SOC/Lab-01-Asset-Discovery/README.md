# Lab 01 - Asset Discovery

## Objetivo

Identificar y clasificar los activos presentes en una red local mediante técnicas de descubrimiento activo. Este laboratorio tiene como propósito obtener visibilidad inicial del entorno, identificar equipos conectados, servicios expuestos y establecer una línea base que sirva como punto de partida para actividades de monitoreo, Threat Hunting y respuesta a incidentes.

---

# Escenario

En una red doméstica utilizada como laboratorio se realizó un proceso de descubrimiento de activos utilizando herramientas de reconocimiento de red desde un equipo Kali Linux.

El objetivo fue identificar:

* Equipos activos.
* Direcciones IP utilizadas.
* Direcciones MAC.
* Fabricantes de dispositivos.
* Servicios disponibles.
* Sistema operativo estimado.
* Dispositivos que podrían representar un riesgo de seguridad.

---

# Entorno del Laboratorio

| Componente          | Descripción                 |
| ------------------- | --------------------------- |
| Host de Análisis    | Kali Linux                  |
| Red                 | LAN doméstica               |
| Objetivo            | Equipos conectados a la red |
| Tipo de laboratorio | Blue Team                   |

---

# Herramientas Utilizadas

* Nmap
* ARP
* Tcpdump

---

# Metodología

Las actividades realizadas fueron las siguientes:

1. Descubrimiento de hosts activos.
2. Identificación de direcciones IP.
3. Obtención de direcciones MAC.
4. Identificación de fabricantes.
5. Enumeración de servicios.
6. Detección del sistema operativo.
7. Clasificación de activos.

---

# Comandos Ejecutados

## Descubrimiento de hosts

```bash
nmap -sn 192.168.1.0/24
```

---

## Descubrimiento de servicios

```bash
nmap -sV 192.168.1.0/24
```

---

## Detección de sistema operativo

```bash
nmap -O <IP>
```

---

## Descubrimiento mediante ARP

```bash
arp -a
```

---

## Captura de tráfico

```bash
tcpdump -i eth0
```

---

# Evidencias

Las evidencias obtenidas durante el laboratorio incluyen:

* Descubrimiento de hosts activos.
* Direcciones IP identificadas.
* Direcciones MAC.
* Fabricantes detectados.
* Servicios expuestos.
* Capturas de pantalla de los resultados.
* Diagramas de red.

Las capturas y diagramas se almacenan en las carpetas correspondientes del repositorio.

---

# Hallazgos

Durante el proceso de descubrimiento fue posible:

* Identificar todos los equipos activos de la red.
* Clasificar dispositivos por fabricante.
* Identificar servicios disponibles.
* Obtener una línea base del entorno.
* Reconocer activos que deberán ser monitoreados por el SIEM.

---

# Relación con Operaciones SOC

El descubrimiento de activos constituye una actividad fundamental dentro de las operaciones de un SOC, ya que permite:

* Mantener un inventario actualizado de activos.
* Identificar dispositivos no autorizados.
* Priorizar activos críticos.
* Mejorar la cobertura del monitoreo.
* Facilitar investigaciones de seguridad.
* Apoyar actividades de Threat Hunting.

---

# Competencias Desarrolladas

* Asset Discovery
* Asset Inventory
* Network Enumeration
* Service Enumeration
* Operating System Fingerprinting
* Network Visibility
* Blue Team Fundamentals

---

# Próximos Laboratorios Relacionados

* Lab 02 - Sysmon Telemetry Validation
* Lab 03 - Windows Event Analysis
* Lab 04 - Wazuh Security Monitoring

---

# Referencias

* Nmap Documentation
* MITRE ATT&CK Framework
* CIS Controls

