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

Se instalarán tres nodos Proxmox VE para formar un clúster de virtualización, permitiendo centralizar la administración de máquinas virtuales y contenedores, así como distribuir los recursos entre los diferentes nodos.

Cada nodo tendrá una dirección IP estática dentro de la red `192.168.25.0/24`.

| **Parámetro** | **Nodo 1** | **Nodo 2** | **Nodo 3** |
|---|---|---|---|
| Nombre | `pve-node1` | `pve-node2` | `pve-node3` |
| Versión |  v9.2 |  v9.2 |  v9.2 |
| IP de gestión | `192.168.25.11/24` | `192.168.25.12/24` | `192.168.25.13/24` |
| Gateway | `192.168.25.1` | `192.168.25.1` | `192.168.25.1` |

### Plan de direccionamiento

- **Red:** `192.168.25.0/24`
- **Gateway principal:** `192.168.25.1` (MikroTik CHR).
- **Nodo Proxmox 1:** `192.168.25.11`
- **Nodo Proxmox 2:** `192.168.25.12`
- **Nodo Proxmox 3:** `192.168.25.13`
- **Máscara:** `255.255.255.0`

Las direcciones se configurarán de forma estática para garantizar que cada nodo mantenga siempre la misma IP dentro de la infraestructura.
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
| IP WAN | `192.168.25.248` |
| Obtención WAN | DHCP |
| Interfaz LAN | `em1` |

## 6. Instalación de Debian NFT

| Parámetro | Valor |
|---|---|
| Sistema | Debian |
| Interfaz principal | `enp0s3` |
| Configuración IP | `192.168.25.40` |
| Firewall | nftables |
| Modo de administración | Consola |

## 7. Instalación de TrueNAS

| Parámetro | Valor |
|---|---|
| Nombre | `TRUENAS_ISO_FHW` |
| Sistema | TrueNAS |
| Dirección inicial | DHCP |
| Dirección prevista | `192.168.25.247` |
| Función | Almacenamiento |

## 8. Instalación de Windows Server

| Parámetro | Valor |
|---|---|
| Sistema | Windows Server 2025 |
| Versión | 10.0.26100 |
| Nombre del equipo | Windows-srv |
| IP | `192.168.25.14` |
| Servicios | Active Directory |

## 9. Instalación del cliente Windows

| Parámetro | Valor |
|---|---|
| Sistema | Windows 11 PRO |
| Nombre del equipo | Windows-cli |
| IP | DHCP |
| Puerta de enlace | IP Mikrotik |
| DNS | Según servicios implantados |


## 10. Instalación del cliente Debian

| Parámetro | Valor |
|---|---|
| Sistema | Debian 13 |
| Nombre del equipo | Debian-cli |
| IP | DHCP |
| Puerta de enlace | IP Mikrotik |
| DNS | Según servicios implantados |

## 11. Registro de incidencias

| Incidencia | Solución aplicada | Estado |
|---|---|---|
| Problemas de conectividad | Revisar adaptadores y direccionamiento | Comprobado |
| Problemas de acceso a Internet en Debian | Revisar gateway, DNS y NAT | Comprobado |


