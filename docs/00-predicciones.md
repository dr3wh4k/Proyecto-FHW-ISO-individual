# 00 — Predicciones iniciales

## 1. Objetivo

Antes de comenzar el despliegue de la infraestructura, se establecen una serie de predicciones sobre el funcionamiento de los sistemas y servicios que formarán parte del laboratorio.

Estas predicciones permitirán comparar los resultados esperados con los resultados obtenidos.

## 2. Predicciones de infraestructura

| Elemento | Predicción |
|---|---|
| MikroTik CHR | Proporcionará conectividad a la red LAN y asignación DHCP. |
| OPNsense | Filtrará el tráfico entre su interfaz WAN y su red LAN interna. |
| Proxmox VE | Permitirá administrar tres nodos de virtualización. |
| TrueNAS | Proporcionará almacenamiento centralizado. |
| Debian | Permitirá aplicar reglas de filtrado mediante nftables. |
| Windows Server | Proporcionará servicios de infraestructura y administración. |
| Cliente Windows | Permitirá comprobar el acceso a los servicios de red. |

## 3. Predicciones de red

La red principal utilizará el segmento:

`192.168.25.0/24`

Se espera que:

- MikroTik utilice `192.168.25.1` como puerta de enlace de la red principal.
- MikroTik proporcione direcciones IP mediante DHCP.
- OPNsense obtenga la dirección `192.168.25.249` en su interfaz WAN.
- Los equipos conectados a la red principal puedan obtener configuración IP automáticamente.
- La LAN de OPNsense permita crear un segmento interno independiente.

## 4. Riesgos previstos

| Riesgo | Consecuencia | Medida preventiva |
|---|---|---|
| Conflictos de IP | Pérdida de conectividad | Planificar las direcciones estáticas. |
| Errores DHCP | Los equipos no reciben IP | Revisar el servidor DHCP del MikroTik. |
| Problemas DNS | No se resuelven dominios | Comprobar DNS y conectividad. |
| Configuración incorrecta de OPNsense | Pérdida de acceso a la LAN | Revisar las interfaces WAN y LAN. |
| Recursos insuficientes | Bajo rendimiento | Ajustar RAM, CPU y almacenamiento. |
| Problemas de virtualización anidada | Las máquinas no arrancan correctamente | Revisar la configuración de VirtualBox. |

## 5. Resultado esperado

Se espera disponer de una infraestructura funcional que permita administrar máquinas virtuales, proporcionar servicios de red, centralizar almacenamiento y aplicar medidas de seguridad.

Las predicciones se revisarán al finalizar las pruebas.
