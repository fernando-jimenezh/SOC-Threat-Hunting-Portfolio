# Lab-01 - Building the Blue Team Lab

## Descripción

Este laboratorio documenta la construcción de la infraestructura base que servirá como plataforma para el desarrollo de prácticas de **SOC Operations**, **Threat Hunting**, **Detection Engineering**, **Incident Response** y **Purple Team**.

El objetivo fue diseñar un entorno de laboratorio estable, aislado y escalable, similar al utilizado en un **Security Operations Center (SOC)**, permitiendo comprender el funcionamiento de cada uno de sus componentes antes de comenzar la incorporación de telemetría y el desarrollo de casos de uso.

---

# Objetivos

* Diseñar la arquitectura del laboratorio.
* Implementar la infraestructura virtual.
* Configurar la topología de red.
* Implementar el servidor Wazuh como plataforma SIEM.
* Preparar los endpoints Windows y Linux para su futura incorporación.
* Validar la conectividad y funcionamiento de toda la infraestructura.

---

# Arquitectura del laboratorio

La infraestructura se implementó sobre **Oracle VirtualBox** utilizando cuatro máquinas virtuales.

Cada equipo dispone de dos interfaces de red:

**Adaptador 1**

* NAT
* Acceso a Internet
* Dirección IP dinámica (DHCP)

**Adaptador 2**

* Host-Only
* Comunicación interna del laboratorio
* Dirección IP estática

La red privada utilizada es:

**192.168.57.0/24**

Esta configuración permite mantener el laboratorio completamente aislado, conservando simultáneamente el acceso a Internet para la instalación y actualización de software.

---

# Infraestructura implementada

## Hipervisor

* Oracle VirtualBox

## Plataforma SIEM

* Wazuh Manager
* Wazuh Indexer
* Wazuh Dashboard

## Topología de red

* NAT
* Host-Only

---

# Equipos del laboratorio

## Wazuh Server

**Hostname**

wazuh

**Dirección IP**

192.168.57.10

**Funciones**

* Wazuh Manager
* Wazuh Indexer
* Wazuh Dashboard

**Estado**

Operativo.

---

## Windows 11 Lab

**Hostname**

win11-lab

**Dirección IP**

192.168.57.20

**Rol**

Endpoint Windows destinado a la generación de telemetría, monitoreo de eventos y simulación de actividades propias de un entorno empresarial.

**Estado**

Preparado para su incorporación al SIEM.

---

## Ubuntu Lab

**Hostname**

ubuntu-lab

**Dirección IP**

192.168.57.30

**Rol**

Endpoint Linux destinado al monitoreo de eventos del sistema, autenticación y auditoría.

**Estado**

Preparado para su incorporación al SIEM.

---

## Kali Linux

**Hostname**

kali

**Dirección IP**

192.168.57.100

**Rol**

Equipo destinado a la simulación controlada de ataques y generación de actividad para ejercicios de detección e investigación.

**Estado**

Operativo.

---

# Validaciones realizadas

Se realizaron las siguientes comprobaciones para garantizar el correcto funcionamiento del laboratorio:

* Inicio correcto de todas las máquinas virtuales.
* Configuración de direcciones IP estáticas.
* Comunicación entre todos los equipos mediante ICMP.
* Acceso a Internet utilizando NAT.
* Comunicación interna utilizando la red Host-Only.
* Funcionamiento correcto del servidor Wazuh.
* Acceso al Dashboard.
* Disponibilidad de la infraestructura para futuras integraciones.

Todas las validaciones fueron satisfactorias.

---

# Estado final del laboratorio

Al finalizar este laboratorio se dispone de una infraestructura completamente funcional compuesta por un servidor Wazuh y tres endpoints preparados para su integración.

La plataforma se encuentra lista para comenzar la incorporación de agentes, la recolección de telemetría y el desarrollo de laboratorios enfocados en monitoreo, detección e investigación de eventos de seguridad.

---

# Objetivos de aprendizaje

La infraestructura implementada permitirá desarrollar experiencia práctica en las siguientes áreas:

* SOC Operations
* SIEM Administration
* Threat Hunting
* Detection Engineering
* Incident Response
* MITRE ATT&CK
* Windows Security
* Linux Security
* Digital Forensics (Básico)
* Purple Team

---

# Lecciones aprendidas

La construcción del laboratorio permitió comprender la importancia de establecer una infraestructura sólida antes de incorporar herramientas de monitoreo y seguridad.

La separación del tráfico mediante interfaces **NAT** y **Host-Only** proporciona un entorno aislado, seguro y fácilmente administrable para la realización de pruebas.

Asimismo, el uso de direccionamiento IP estático simplifica la administración de los equipos y facilita la integración entre los diferentes componentes del laboratorio.

Este laboratorio constituye la base sobre la cual se desarrollarán todas las investigaciones, casos de uso y ejercicios prácticos documentados en este portafolio.
