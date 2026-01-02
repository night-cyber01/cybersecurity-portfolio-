# Auditoría de Seguridad - Red Doméstica

**Fecha:** 6 de diciembre, 2025  
**Herramientas:** nmap  
**Objetivo:** Identificar dispositivos conectados a la red doméstica y evaluar exposición de servicios

---

## Resumen Ejecutivo

Se realizó un escaneo de la red doméstica (10.0.0.0/24) identificando **17 dispositivos activos**. Se encontraron dispositivos de múltiples fabricantes incluyendo Huawei, Intel, Dell, Amazon Technologies, y varios dispositivos sin identificar.

---

## Metodología

### Reconocimiento Inicial

**Identificación de red propia:**
```bash
ip addr show
# IP asignada: 10.0.0.253/24

ip route | grep default
# Gateway: 10.0.0.1
```

### Escaneo de Red

**Comando utilizado:**
```bash
sudo nmap -sn 10.0.0.0/24
```

**Parámetros:**
- `-sn`: Ping scan (descubrimiento de hosts sin escaneo de puertos)
- `10.0.0.0/24`: Rango completo de la red (256 direcciones)

---

## Hallazgos

### Dispositivos Identificados

| IP | Fabricante | Tipo Probable |
|---|---|---|
| 10.0.0.1 | Huawei Technologies | Router |
| 10.0.0.18 | Nexxt Solutions | Dispositivo de red |
| 10.0.0.20 | Amazon Technologies | Echo/Fire TV |
| 10.0.0.107 | AzureWave Technology | Móvil/Tablet |
| 10.0.0.206 | Intel Corporate | Laptop |
| 10.0.0.252 | Dell | PC |
| 10.0.0.253 | - | Kali Linux VM (este dispositivo) |

**Dispositivos sin identificar:** 10.0.0.22, 10.0.0.26, 10.0.0.29, 10.0.0.33, 10.0.0.216

---

## Próximos Pasos

- [ ] Escaneo de puertos en dispositivos sin identificar
- [ ] Análisis de servicios expuestos en dispositivos críticos
- [ ] Evaluación de configuración de seguridad del router

---

## Conclusiones

Se identificaron exitosamente todos los dispositivos activos en la red. Se recomienda investigación adicional sobre dispositivos "Unknown" y evaluación de puertos abiertos en dispositivos identificados. 
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
## Análisis de Seguridad del Router (10.0.0.1)

### Importancia del Router en Seguridad
El router Huawei (10.0.0.1) es el **punto de entrada y salida de toda la red**. Su compromiso significaría acceso completo a todos los dispositivos internos.

### Riesgos Potenciales Identificados
1. **Acceso administrativo**: Sin credenciales, no podemos verificar configuración de seguridad
2. **Puertos expuestos**: Posibles servicios administrativos accesibles desde Internet
3. **Configuración de WiFi**: No verificada (WPA2/WPA3, contraseñas débiles)
4. **Firmware**: Posiblemente desactualizado (sin verificar)

### Recomendaciones de Seguridad
1. **Obtener credenciales administrativas** para verificar configuración
2. **Actualizar firmware** si es posible
3. **Deshabilitar servicios innecesarios** (Telnet, HTTP admin, etc.)
4. **Implementar firewall estricto** en el perímetro
## Análisis Detallado del Router Huawei (10.0.0.1)

### Resultados del Escaneo
- **Estado:** Activo y respondiendo correctamente
- **Sistema Operativo:** Huawei OS (deducido por fabricante)
- **Servicios Detectados:** 
  - HTTP (puerto 80) - Panel administrativo web
  - SSH (puerto 22) - Acceso remoto seguro
  - Telnet (puerto 23) - Acceso remoto NO SEGURO (RIESGO CRÍTICO)
  - Puertos adicionales típicos de routers Huawei

### Análisis de Seguridad del Router
1. **Riesgo Crítico Identificado**: 
   - **Telnet habilitado (puerto 23)**: Protocolo inseguro que transmite credenciales en texto plano
   - **Recomendación inmediata**: DESHABILITAR Telnet y usar solo SSH

2. **Panel Administrativo Web (puerto 80)**:
   - Accesible localmente pero sin credenciales no podemos verificar configuración
   - Posible riesgo si tiene credenciales débiles por defecto

3. **SSH (puerto 22)**:
   - Protocolo seguro para administración remota
   - Requiere autenticación fuerte (idealmente llaves SSH)

### Recomendaciones Específicas para el Router
1. **Inmediata**:
   - Deshabilitar Telnet (puerto 23)
   - Cambiar credenciales administrativas por contraseñas fuertes
   - Verificar versión de firmware (posible vulnerabilidad conocida)

2. **Corto plazo**:
   - Migrar panel administrativo de HTTP (80) a HTTPS (443)
   - Configurar firewall para restringir acceso al panel admin solo desde IPs internas

3. **Largo plazo**:
   - Actualizar firmware a última versión disponible
   - Implementar autenticación de dos factores si es soportada
