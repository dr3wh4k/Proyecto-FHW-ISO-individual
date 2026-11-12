# 05 — Instalación de la plataforma

## 1. Objetivo

Documentar el proceso de instalación de los sistemas y servicios que forman parte de la infraestructura.

## 2. Entorno de virtualización

### VirtualBox

- Software: Oracle VirtualBox.
- Versión: Pendiente de documentar.
- Sistema anfitrión: Pendiente de documentar.
- Memoria RAM disponible: Pendiente.
- Almacenamiento disponible: Pendiente.

## 3. Instalación de Proxmox VE

Se instalarán tres nodos Proxmox VE para formar un entorno de virtualización.

| Parámetro | Nodo 1 | Nodo 2 | Nodo 3 |
|---|---|---|---|
| Nombre | Pendiente | Pendiente | Pendiente |
| Versión | Pendiente | Pendiente | Pendiente |
| IP de gestión | Pendiente | Pendiente | Pendiente |
| Gateway | Pendiente | Pendiente | Pendiente |
| DNS | Pendiente | Pendiente | Pendiente |
| CPU | Pendiente | Pendiente | Pendiente |
| RAM | Pendiente | Pendiente | Pendiente |
| Disco | Pendiente | Pendiente | Pendiente |

### Consideraciones

- Activar la virtualización anidada cuando sea necesaria.
- Comprobar la conectividad de red.
- Configurar una IP fija para cada nodo.
- Utilizar nombres de host diferentes.
- Verificar la sincronización horaria.
- Comprobar la comunicación entre los tres nodos.

## 4. Instalación de MikroTik CHR

| Parámetro | Valor |
|---|---|
| Sistema | RouterOS CHR |
| Interfaz LAN | `ether2` |
| IP LAN | `192.168.25.1/24` |
| Interfaz WAN | `ether3` |
| Función | Router principal y DHCP |

## 5. Instalación de OPNsense

| Parámetro | Valor |
|---|---|
| Sistema | OPNsense |
| Interfaz WAN | `em0` |
| IP WAN | `192.168.25.249` |
| Obtención WAN | DHCP |
| Interfaz LAN | `em1` |
| IP LAN | Pendiente de confirmar |

## 6. Instalación de Debian

| Parámetro | Valor |
|---|---|
| Sistema | Debian |
| Interfaz principal | `enp0s3` |
| Configuración IP | DHCP |
| Firewall | nftables |
| Modo de administración | Consola |

## 7. Instalación de TrueNAS

| Parámetro | Valor |
|---|---|
| Nombre | `TRUENAS_ISO_FHW` |
| Sistema | TrueNAS |
| Dirección inicial | DHCP |
| Dirección prevista | `192.168.25.200` |
| Función | Almacenamiento |

## 8. Instalación de Windows Server

| Parámetro | Valor |
|---|---|
| Sistema | Windows Server |
| Versión | Pendiente de documentar |
| Nombre del equipo | Pendiente |
| IP | Pendiente |
| Servicios | Pendiente de definir |

## 9. Instalación del cliente Windows

| Parámetro | Valor |
|---|---|
| Sistema | Windows |
| Nombre del equipo | Pendiente |
| IP | Pendiente |
| Puerta de enlace | Según segmento de red |
| DNS | Según servicios implantados |

## 10. Registro de incidencias

| Incidencia | Solución aplicada | Estado |
|---|---|---|
| Problemas de arranque de máquinas virtuales | Pendiente de documentar | Pendiente |
| Problemas de conectividad | Revisar adaptadores y direccionamiento | En revisión |
| Problemas de acceso a Internet en Debian | Revisar gateway, DNS y NAT | En revisión |

## 11. Evidencias

Añadir capturas de:

- Instalación de Proxmox.
- Configuración de los tres nodos.
- Instalación de MikroTik.
- Configuración de OPNsense.
- Instalación de Debian.
- Instalación de TrueNAS.
- Instalación de Windows Server.
- Instalación del cliente Windows.
