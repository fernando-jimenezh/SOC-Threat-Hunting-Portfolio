# Lab-02 | Validación de Endpoints Windows y Linux

## Objetivo

El objetivo de este laboratorio fue validar completamente la integración de los Endpoints Windows y Linux con la plataforma Wazuh SIEM, verificando el funcionamiento del proceso de Enrollment, la comunicación con el Manager, la recepción de telemetría y el estado operativo de los agentes antes de comenzar las fases de Detection Engineering y Threat Hunting.

Durante este laboratorio no solo se verificó que los agentes estuvieran instalados, sino que se realizó un proceso completo de diagnóstico y resolución de problemas similar al utilizado en un entorno SOC real.

---

# Objetivos específicos

- Validar la comunicación entre los Endpoints y el Wazuh Manager.
- Verificar el proceso de Enrollment.
- Confirmar el Heartbeat de los agentes.
- Validar la recepción de telemetría.
- Verificar la integración de Sysmon en Windows.
- Validar la recolección de logs nativos de Linux.
- Resolver problemas de configuración encontrados durante la implementación.

---

# Infraestructura

| Equipo | Dirección IP | Función |
|---------|-------------|---------|
| Wazuh Manager | 192.168.57.10 | SIEM Manager |
| Windows 11 | 192.168.57.20 | Endpoint Windows |
| Ubuntu 22.04 | 192.168.57.30 | Endpoint Linux |

---

# Arquitectura

```
                 +----------------------+
                 |   Wazuh Dashboard    |
                 +----------+-----------+
                            |
                 +----------+-----------+
                 |      Wazuh Manager   |
                 +----------+-----------+
                            |
        -----------------------------------------
        |                                       |
+---------------------+               +---------------------+
| Windows 11 Endpoint |               | Ubuntu Endpoint     |
| Wazuh Agent         |               | Wazuh Agent         |
| Sysmon              |               | auth.log            |
| Event Logs          |               | syslog              |
+---------------------+               +---------------------+
```

---

# Componentes validados

## Windows Endpoint

Se validó correctamente:

- Wazuh Agent
- Enrollment
- Heartbeat
- Sysmon
- Windows Event Logs
- Security Log
- Application Log
- System Log
- Task Scheduler
- Comunicación con el Manager
- Recepción de telemetría

---

## Ubuntu Endpoint

Se validó correctamente:

- Wazuh Agent
- Heartbeat
- Comunicación con el Manager
- auth.log
- syslog
- kern.log
- dpkg.log
- Syscollector
- Security Configuration Assessment (SCA)
- File Integrity Monitoring (FIM)

---

# Problemas encontrados

## Problema 1

### Windows

El agente permanecía en estado **Disconnected**.

### Diagnóstico

Se revisó:

- Estado del servicio.
- Configuración del archivo ossec.conf.
- Conectividad TCP.
- Logs del agente.
- Registro del agente.

### Causa

El proceso de Enrollment no había finalizado correctamente.

### Solución

Se registró nuevamente el agente y se verificó la recepción de una nueva Agent Key.

Resultado:

- Endpoint Active.
- Heartbeat operativo.
- Telemetría recibida correctamente.

---

## Problema 2

### Ubuntu

El agente intentaba conectarse a una dirección IP antigua.

```
192.168.56.10
```

### Diagnóstico

El archivo:

```
/var/ossec/etc/ossec.conf
```

mantenía la configuración anterior del laboratorio.

### Solución

Se actualizó la dirección del Manager:

```
192.168.57.10
```

Posteriormente se reinició el servicio:

```
systemctl restart wazuh-agent
```

Resultado:

El agente comenzó a comunicarse correctamente con el Manager.

---

## Problema 3

Durante las pruebas se generaron mensajes:

- Duplicate name
- Agent key already in use

Estos mensajes permitieron comprender el funcionamiento interno del proceso de Enrollment, la administración de Agent Keys y la sincronización entre authd y remoted.

---

# Validaciones realizadas

Se verificó correctamente:

- Wazuh Agent instalado.
- Servicio operativo.
- Comunicación con el Manager.
- Enrollment.
- Heartbeat.
- Agent Keys.
- Recepción de telemetría.
- Dashboard.
- Sysmon.
- Event Logs.
- auth.log.
- syslog.
- kern.log.
- Syscollector.
- Security Configuration Assessment.

---

# Evidencias

Durante este laboratorio se obtuvieron evidencias de:

- Dashboard mostrando ambos Endpoints activos.
- Agent Control.
- Logs del agente Windows.
- Logs del agente Linux.
- Configuración de ossec.conf.
- Integración de Sysmon.
- Telemetría Windows.
- Telemetría Linux.

---

# Conocimientos adquiridos

Este laboratorio permitió comprender el funcionamiento interno de los siguientes componentes:

- Wazuh Agent
- Wazuh Manager
- Enrollment
- Agent Keys
- Heartbeat
- File Integrity Monitoring
- Syscollector
- Security Configuration Assessment
- Sysmon
- Windows Event Logs
- Linux Log Collection
- Diagnóstico mediante ossec.log
- Validación de conectividad entre Manager y Endpoints

---

# Resultado

Al finalizar este laboratorio se logró disponer de una plataforma completamente operativa con dos Endpoints integrados al SIEM:

- Windows 11
- Ubuntu 22.04

Ambos enviando telemetría al Wazuh Manager y listos para comenzar la siguiente etapa del proyecto orientada a Telemetry Collection, Detection Engineering y Threat Hunting.
