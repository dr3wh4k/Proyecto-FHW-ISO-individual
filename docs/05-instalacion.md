# 05 — Instalación y configuración de la plataforma

## 1. Objetivo

Documentar el proceso de instalación y configuración de los sistemas operativos, servidores y servicios que forman parte de la infraestructura del proyecto ISO-FHW.

El entorno se ha desplegado mediante máquinas virtuales en Oracle VirtualBox, utilizando una red interna para permitir la comunicación entre los diferentes equipos.

La infraestructura incluye un clúster de virtualización Proxmox, servidores de comunicaciones, almacenamiento, servicios de directorio y equipos cliente.

## 2. Entorno de virtualización

### Oracle VirtualBox

Se ha utilizado Oracle VirtualBox como plataforma de virtualización para desplegar y administrar los diferentes sistemas del proyecto.

| Parámetro | Valor |
|---|---|
| Software | Oracle VirtualBox |
| Versión | 7.0.16 |
| Sistema anfitrión | Pendiente de documentar |
| Memoria RAM disponible | Pendiente de documentar |
| Almacenamiento disponible | Pendiente de documentar |
| Tipo de red | Red interna |
| Direccionamiento | `192.168.25.0/24` |

### Configuración de red

Se ha establecido una red interna para conectar las máquinas virtuales y permitir la comunicación entre los servidores y los clientes.

El direccionamiento utiliza la siguiente configuración:

- **Red:** `192.168.25.0/24`
- **Máscara:** `255.255.255.0`
- **Gateway principal:** `192.168.25.1`
- **Router principal:** MikroTik CHR.

Las direcciones IP de los servidores se han configurado principalmente de forma estática, mientras que los equipos cliente utilizan DHCP.

---

## 3. Instalación de Proxmox VE

Se han instalado tres nodos Proxmox VE para formar un clúster de virtualización. Su finalidad es centralizar la administración de máquinas virtuales y contenedores, además de facilitar la distribución de recursos entre los diferentes nodos.

### Configuración de los nodos

| Parámetro | Nodo 1 | Nodo 2 | Nodo 3 |
|---|---|---|---|
| Nombre | `pve-node1` | `pve-node2` | `pve-node3` |
| Versión | 9.2 | 9.2 | 9.2 |
| IP de gestión | `192.168.25.11` | `192.168.25.12` | `192.168.25.13` |
| Gateway | `192.168.25.1` | `192.168.25.1` | `192.168.25.1` |
| Máscara | `/24` | `/24` | `/24` |

<img width="1466" height="840" alt="CLUSTER FINAL 3 NODOS" src="https://github.com/user-attachments/assets/5eaa6e78-42bc-442f-8080-c106e5de754a" />


### Configuración y comprobaciones

Durante la instalación se han realizado las siguientes tareas:

- Instalación de Proxmox VE en los tres nodos.
- Asignación de nombres de host diferentes.
- Configuración de direcciones IP estáticas.
- Configuración del gateway principal.
- Comprobación de conectividad entre los nodos.
- Creación del clúster Proxmox.
- Incorporación de los nodos adicionales al clúster.
- Comprobación de la comunicación entre los tres servidores.

**Resultado:** Se ha conseguido crear un clúster formado por tres nodos Proxmox VE.

---

## 4. Instalación de MikroTik CHR

Se ha instalado MikroTik CHR utilizando RouterOS como sistema operativo de enrutamiento. Este equipo actúa como router principal de la infraestructura y proporciona direccionamiento IP automático a los clientes mediante DHCP.

### Configuración

| Parámetro | Valor |
|---|---|
| Sistema | MikroTik CHR |
| Sistema operativo | RouterOS |
| Interfaz LAN | `ether2` |
| IP LAN | `192.168.25.1/24` |
| Interfaz WAN | `ether3` |
| Función | Enrutamiento y servidor DHCP |

<img width="721" height="402" alt="MIKROTIK CONFIG + PING" src="https://github.com/user-attachments/assets/cdf0a7d4-f544-40d0-bf61-59d581b1b9b6" />


### Servicios y funcionalidades

- Enrutamiento entre redes.
- Asignación automática de direcciones IP mediante DHCP.
- Puerta de enlace predeterminada de los clientes.
- Comunicación entre los equipos de la red interna.
- Salida hacia redes externas mediante la interfaz WAN, según la configuración de NAT.

---

## 5. Instalación de OPNsense

Se ha instalado OPNsense como sistema de firewall y seguridad de red, utilizando dos interfaces de red para separar la conexión WAN de la LAN.

### Configuración

| Parámetro | Valor |
|---|---|
| Sistema | OPNsense |
| Interfaz WAN | `em0` |
| IP WAN | `192.168.25.248` |
| Obtención de IP WAN | DHCP |
| Interfaz LAN | `em1` |
| Función | Firewall y seguridad de red |

<img width="748" height="493" alt="IP OPNSENSE" src="https://github.com/user-attachments/assets/005def77-1167-42b2-bf8a-c850be71bc21" />


### Comprobaciones

- Instalación correcta del sistema.
- Detección de las interfaces de red.
- Configuración de las interfaces WAN y LAN.
- Acceso a la administración del firewall.
- Comprobación del funcionamiento de las interfaces.

**Resultado:** La instalación y configuración inicial de OPNsense se completaron correctamente, sin incidencias destacables.

---

## 6. Instalación de Debian con nftables

Se ha instalado Debian como servidor de comunicaciones y seguridad, utilizando nftables para implementar las reglas de filtrado y control del tráfico de red.

A diferencia de otros servidores, su administración se realiza exclusivamente mediante consola.

### Configuración

| Parámetro | Valor |
|---|---|
| Sistema operativo | Debian |
| Interfaz principal | `enp0s3` |
| Dirección IP | `192.168.25.40/24` |
| Gateway | `192.168.25.1` |
| Firewall | nftables |
| Administración | Consola |

<img width="1266" height="603" alt="DEBIAN NFT IP" src="https://github.com/user-attachments/assets/808e11a7-44f3-4fa6-aa06-18a8762e1f0a" />


### Configuración y comprobaciones

- Instalación del sistema operativo Debian.
- Configuración de la dirección IP estática.
- Configuración de la puerta de enlace.
- Instalación y configuración de nftables.
- Creación de reglas de filtrado de tráfico.
- Comprobación de conectividad con MikroTik.
- Verificación de las comunicaciones de red.

**Resultado:** Se consiguió establecer la comunicación con MikroTik después de corregir la configuración IP y los parámetros de red.

---

## 7. Instalación de TrueNAS

Se ha instalado TrueNAS para proporcionar almacenamiento centralizado dentro de la infraestructura.

Este servidor permite gestionar el almacenamiento y configurar diferentes sistemas de organización y protección de datos, incluyendo RAID.

### Configuración

| Parámetro | Valor |
|---|---|
| Nombre del equipo | `TRUENAS_ISO_FHW` |
| Sistema | TrueNAS |
| Dirección IP inicial | DHCP |
| Dirección IP final | `192.168.25.247` |
| Función | Almacenamiento centralizado |

### Configuración y comprobaciones

- Instalación de TrueNAS.
- Configuración de la dirección IP de administración.
- Acceso a la interfaz web.
- Preparación de los dispositivos de almacenamiento.
- Configuración y comprobación de diferentes niveles RAID.

**Resultado:** Se dispone de un servidor de almacenamiento accesible desde la red interna.

---

## 8. Instalación de Windows Server

Se ha instalado Windows Server 2025 para proporcionar servicios de directorio y administración centralizada de los equipos del entorno.

Se ha configurado Active Directory Domain Services (AD DS) para crear un dominio y permitir la gestión de usuarios, equipos y recursos de red.

### Configuración

| Parámetro | Valor |
|---|---|
| Sistema operativo | Windows Server 2025 |
| Versión | 10.0.26100 |
| Nombre del equipo | `Windows-srv` |
| Dirección IP | `192.168.25.14` |
| Servicio principal | Active Directory Domain Services |
| Administración | Interfaz gráfica |

### Configuración y comprobaciones

- Instalación del sistema operativo.
- Configuración de la dirección IP estática.
- Instalación del rol Active Directory Domain Services.
- Promoción del servidor a controlador de dominio.
- Creación y configuración del dominio.
- Comprobación del funcionamiento de Active Directory.

**Resultado:** La instalación y configuración del dominio se realizaron correctamente, sin incidencias durante el proceso.

---

## 9. Instalación del cliente Windows

Se ha instalado Windows 11 Pro como equipo cliente para comprobar los servicios proporcionados por los servidores de la infraestructura.

### Configuración

| Parámetro | Valor |
|---|---|
| Sistema operativo | Windows 11 Pro |
| Nombre del equipo | `Windows-cli` |
| Dirección IP | DHCP |
| Puerta de enlace | `192.168.25.1` |
| DNS | Servidor DNS de Active Directory |

### Comprobaciones

- Obtención automática de dirección IP mediante DHCP.
- Comprobación de conectividad con MikroTik.
- Verificación de la puerta de enlace.
- Comprobación de resolución DNS.
- Preparación para la integración con el dominio.

---

## 10. Instalación del cliente Debian

Se ha instalado Debian 13 como segundo equipo cliente de la infraestructura. Su objetivo es comprobar la conectividad y el funcionamiento de los servicios de red desde un sistema Linux.

### Configuración

| Parámetro | Valor |
|---|---|
| Sistema operativo | Debian 13 |
| Nombre del equipo | `Debian-cli` |
| Dirección IP | DHCP |
| Puerta de enlace | `192.168.25.1` |
| DNS | Servidor DNS configurado en la infraestructura |
| Administración | Consola |

### Comprobaciones

- Obtención automática de dirección IP.
- Comprobación de conectividad con MikroTik.
- Verificación de la puerta de enlace.
- Comprobación de resolución DNS.
- Comunicación con los diferentes servidores.

---

## 11. Registro de incidencias

Durante el despliegue de la infraestructura se produjeron algunas incidencias relacionadas principalmente con la configuración de red y los adaptadores de VirtualBox.

| Equipo | Incidencia detectada | Solución aplicada | Estado |
|---|---|---|---|
| MikroTik CHR | No proporcionaba conectividad a los equipos cliente. | Revisión de interfaces, configuración LAN y servicio DHCP. | Resuelto |
| Proxmox VE | Los nodos estaban configurados en NAT en lugar de red interna, por lo que no recibían ni respondían a los ping de la infraestructura. | Cambio del adaptador de red a modo red interna y revisión del direccionamiento. | Resuelto |
| Windows Server | No se produjeron incidencias durante la instalación y creación del dominio. | No fue necesario aplicar soluciones. | Correcto |
| Debian nftables | No conseguía comunicarse con MikroTik debido a problemas de configuración IP. | Corrección de la dirección IP y configuración de red. | Resuelto |
| OPNsense | No se produjeron incidencias destacables durante la instalación. | No fue necesario aplicar soluciones adicionales. | Correcto |
| Clientes Windows y Debian | Se realizaron comprobaciones de conectividad y obtención automática de direcciones IP. | Configuración y comprobación del servicio DHCP y los parámetros de red. | Comprobado |

---

## 12. Resultado final

Una vez finalizadas las instalaciones y configuraciones, se dispone de una infraestructura virtualizada compuesta por:

- **3 nodos Proxmox VE:** clúster de virtualización.
- **1 MikroTik CHR:** router principal y servidor DHCP.
- **1 OPNsense:** firewall y seguridad de red.
- **1 Debian nftables:** servidor de comunicaciones y filtrado de tráfico.
- **1 TrueNAS:** almacenamiento centralizado.
- **1 Windows Server 2025:** servidor de dominio mediante Active Directory.
- **1 cliente Windows 11 Pro:** equipo cliente.
- **1 cliente Debian 13:** equipo cliente Linux.

La infraestructura utiliza el direccionamiento `192.168.25.0/24` y una red interna de VirtualBox para facilitar la comunicación entre los diferentes sistemas.

En conjunto, se ha conseguido desplegar el entorno de virtualización y los principales servicios de red, almacenamiento, seguridad y administración necesarios para el proyecto ISO-FHW.
