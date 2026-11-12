# 02 — Inventario de recursos

## 1. Objetivo

Registrar los recursos hardware y software utilizados para desplegar la infraestructura del proyecto.

## 2. Hardware físico

| Recurso | Características |
|---|---|
| Equipo anfitrión | Pendiente de documentar |
| Procesador | Pendiente de documentar |
| Memoria RAM | Pendiente de documentar |
| Almacenamiento | Pendiente de documentar |
| Adaptador de red | Pendiente de documentar |

## 3. Software utilizado

| Software | Función |
|---|---|
| VirtualBox | Virtualización del laboratorio |
| Proxmox VE | Gestión de la infraestructura virtual |
| MikroTik CHR | Router principal |
| OPNsense | Firewall y comunicaciones |
| Debian | Sistema Linux con nftables |
| TrueNAS | Gestión del almacenamiento |
| Windows Server | Servicios de servidor |
| Windows | Sistema cliente |

## 4. Inventario de máquinas virtuales

| Máquina virtual | Sistema | Función | Estado |
|---|---|---|---|
| MikroTik CHR | RouterOS | Router principal y DHCP | Desplegado |
| OPNsense | OPNsense | Firewall | Desplegado |
| Debian | Debian Linux | Firewall nftables | Desplegado |
| TrueNAS_ISO_FHW | TrueNAS | Almacenamiento | Desplegado |
| Proxmox Nodo 1 | Proxmox VE | Virtualización | Pendiente de completar |
| Proxmox Nodo 2 | Proxmox VE | Virtualización | Pendiente de completar |
| Proxmox Nodo 3 | Proxmox VE | Virtualización | Pendiente de completar |
| Windows Server | Windows Server | Servidor | Pendiente |
| Cliente Windows | Windows | Cliente | Pendiente |

## 5. Direccionamiento IP

| Dispositivo | IP |
|---|---|
| MikroTik LAN | `192.168.25.1` |
| OPNsense WAN | `192.168.25.249` |
| OPNsense LAN | Pendiente de confirmar |
| Debian | DHCP |
| TrueNAS | DHCP |
| TrueNAS (propuesta estática) | `192.168.25.200` |
| Proxmox Nodo 1 | Pendiente |
| Proxmox Nodo 2 | Pendiente |
| Proxmox Nodo 3 | Pendiente |
| Windows Server | Pendiente |
| Cliente Windows | Pendiente |

## 6. Observaciones

Las direcciones IP de los equipos que todavía no tienen configuración definitiva se completarán durante la fase de configuración.

No se asignarán direcciones estáticas sin comprobar previamente el rango DHCP del MikroTik para evitar conflictos.
