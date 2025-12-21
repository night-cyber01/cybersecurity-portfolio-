# Auditoría de Seguridad - Red Doméstica

**Fecha:** 6 de diciembre, 2025  
**Herramientas:** nmap  
**Objetivo:** Identificar dispositivos conectados a la red doméstica y evaluar exposición de servicios

---

## Resumen Ejecutivo

Se realizó un escaneo de la red doméstica (10.0.0.0/24) identificando **17 dispositivos activos**. Se encontraron dispositivos de múltiples fabricantes incluyendo Huawei, Intel, Dell, Amazon Technologies, y varios dispositivos sin identificar.

---

## Metodología

### Reconocimiento I### Actualización 20/12/2025 - Análisis de Dispositivos Críticos
Se realizó un escaneo profundo (-sS -sV -O -p-) sobre los objetivos 10.0.0.252 y 10.0.0.63.

#### Hallazgos:
1. **IP 10.0.0.63 (Servidor de Monitoreo):**
   - Identificado servicio **Nagios NSCA**. Probable cambio de IP del servidor Nagios previamente detectado en .29.
   - **Riesgo:** Puerto 1080 (SOCKS5) abierto. Necesita revisión de autenticación.
   - Presencia de Firewall (49,140 puertos filtrados).

2. **IP 10.0.0.252:**
   - Confirmado como dispositivo móvil (Android 10-12).
   - Servicio `tcpwrapped` detectado; alta restricción de conexión.
