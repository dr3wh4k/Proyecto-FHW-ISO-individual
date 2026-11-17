# 03 — Diseño de red

<img width="1241" height="984" alt="DIAGRAMA ISO-FHW-Page-1 drawio (1)" src="https://github.com/user-attachments/assets/55f3924d-73c5-4536-8f24-f14223ab0f8c" />


## 1. Objetivo

Diseñar la infraestructura de red del laboratorio, identificando los dispositivos de comunicaciones, sus interfaces, las direcciones IP y las conexiones entre los diferentes segmentos.

## 2. Red principal

La red principal del laboratorio utiliza el siguiente direccionamiento:

- Red: `192.168.25.0/24`
- Máscara: `255.255.255.0`
- Puerta de enlace: `192.168.25.1`
- Router principal: MikroTik CHR.
- Servidor DHCP: MikroTik CHR.

## 3. Dispositivos de comunicaciones

### MikroTik CHR

Actúa como router principal de la infraestructura.

| Parámetro | Configuración |
|---|---|
| Interfaz LAN | `ether2` |
| IP LAN | `192.168.25.1/24` |
| Interfaz WAN | `ether3` |
| Función LAN | Puerta de enlace |
| Servicio DHCP | Activo según configuración indicada |

La interfaz `ether3` conecta con la red exterior o red de pruebas.

La interfaz `ether2` proporciona conectividad a la red principal del laboratorio.

### OPNsense

Actúa como cortafuegos y servidor de comunicaciones.

| Parámetro | Configuración |
|---|---|
| Interfaz WAN | `em0` |
| Dirección WAN | `192.168.25.2` |
| Interfaz LAN | `em1` |
| Función | Filtrado y segmentación de red |

La interfaz WAN se conecta a la red principal del MikroTik.

La interfaz LAN se utiliza para crear un segmento interno independiente.

### Debian NFT

Debian forma parte de los sistemas de comunicaciones del proyecto.

| Parámetro | Configuración |
|---|---|
| Interfaz | `enp0s3` |
| Dirección IP | `192.168.25.40` |
| Red esperada | `192.168.25.0/24` |
| Firewall | nftables |

La dirección IP definitiva dependerá de la concesión DHCP del MikroTik.

### TrueNAS

TrueNAS proporciona el servicio de almacenamiento.

| Parámetro | Configuración |
|---|---|
| Nombre de máquina | `TRUENAS_ISO_FHW` |
| Dirección estática | `192.168.25.247` |
| Función | Almacenamiento centralizado |

La dirección estática se configurará cuando se compruebe que está libre y fuera del rango DHCP dinámico.

## 4. Plan de direccionamiento

| Dispositivo | Interfaz | Dirección |
|---|---|---|
| MikroTik | ether2 | 192.168.25.1 |
| OPNsense | em0 | 192.168.25.2 |
| Debian | enp0s3 | 192.168.25.40 |
| TrueNAS | Gestión | 192.168.25.247 |
| Proxmox Nodo 1 | Gestión | 192.168.25.11 |
| Proxmox Nodo 2 | Gestión | 192.168.25.12 |
| Proxmox Nodo 3 | Gestión | 192.168.25.13 |
| Windows Server | Red | 192.168.25.14 |
| Cliente Windows | Red | DHCP |
| Cliente Debian | Red | DHCP |

## 5. Redes de VirtualBox

La configuración de los adaptadores de red de cada máquina virtual deberá documentarse indicando:

- Número de adaptador.
- Tipo de conexión.
- Nombre de la red interna, si corresponde.
- Dirección MAC.
- Interfaz del sistema operativo asociada.

La asignación exacta de adaptadores queda pendiente de completar con la configuración real de VirtualBox.

## 6. Consideraciones de diseño

- La red principal utiliza el MikroTik como puerta de enlace.
- OPNsense recibe conectividad WAN desde la red principal.
- La LAN de OPNsense debe permanecer diferenciada de la red WAN.
- No se deben utilizar subredes solapadas.
- Las IP estáticas deben excluirse del rango DHCP o reservarse en el servidor DHCP.
- Los nodos Proxmox deben tener direcciones fijas para facilitar la administración del clúster.

## 7. Pruebas previstas

- Comprobar la comunicación con `192.168.25.1`.
- Comprobar que OPNsense recibe la IP WAN `192.168.25.2`.
- Comprobar la asignación DHCP a Debian.
- Comprobar el acceso a la interfaz web de TrueNAS.
- Comprobar la comunicación entre los nodos Proxmox.
- Comprobar la conectividad de Windows Server y el cliente Windows.
