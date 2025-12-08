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
