# Auditoría de Red Doméstica - Enero 2, 2026

## Escaneo Detallado de Dispositivos Unknown

### 10.0.0.4
- **MAC Address:** 02:9F:44:D1:4D:A5 (Unknown)
- **Estado:** No responde al escaneo profundo
- **Puertos abiertos:** No detectables
- **Servicios detectados:** Ninguno
- **Sistema operativo:** Desconocido
- **Análisis:** Posiblemente dispositivo apagado o con firewall extremo

### 10.0.0.5
- **MAC Address:** 0A:57:69:42:AE:2E (Unknown)
- **Estado:** Activo pero restrictivo
- **Puertos abiertos:** Ninguno detectable
- **Servicios detectados:** Ninguno (todos puertos cerrados/reset)
- **Sistema operativo:** Desconocido
- **Análisis:** Dispositivo cliente en modo sleep o con firewall local

### 10.0.0.23
- **MAC Address:** 1A:7D:6D:A0:BE:60 (Unknown)
- **Estado:** Activo con firewall agresivo
- **Puertos abiertos:** Todos filtrados (no-response)
- **Servicios detectados:** No identificables
- **Sistema operativo:** Desconocido
- **Análisis:** Firewall bloquea todos los escaneos - dispositivo protegido

### 10.0.0.36
- **MAC Address:** E6:5F:7F:85:4C:5C (Unknown)
- **Estado:** Activo con servicios limitados
- **Puertos abiertos:** 5060/tcp (cerrado)
- **Servicios detectados:** SIP (Session Initiation Protocol - VoIP)
- **Sistema operativo:** Posibles candidatos:
  - Billion 7404VGP-M ADSL router
  - D-Link DFL-700 firewall
  - Linux 2.6.x (muy antiguo)
- **Análisis:** Dispositivo de red probablemente relacionado con telefonía VoIP

### 10.0.0.38
- **MAC Address:** 4A:2C:9F:33:3D:E8 (Unknown)
- **Estado:** Activo con firewall agresivo
- **Puertos abiertos:** Todos filtrados (no-response)
- **Servicios detectados:** No identificables
- **Sistema operativo:** Desconocido
- **Análisis:** Firewall bloquea todos los escaneos - dispositivo protegido
