# Diagrama lógico

<img width="3490" height="1664" alt="mermaid-diagram" src="https://github.com/user-attachments/assets/fb2eb580-1593-4ebe-b7c2-ac879b65c4ab" />


### Arquitectura de la infraestructura

La infraestructura del proyecto ISO-FHW está desplegada mediante Oracle VirtualBox, utilizando una red interna con direccionamiento `192.168.25.0/24`.

El MikroTik CHR actúa como router principal, proporcionando conectividad y asignación automática de direcciones IP mediante DHCP.

La infraestructura incorpora tres nodos Proxmox VE que forman un clúster de virtualización, junto con diferentes servidores especializados en comunicaciones, seguridad, almacenamiento y administración de usuarios.

OPNsense y Debian con nftables proporcionan funcionalidades de seguridad y filtrado de tráfico. TrueNAS centraliza el almacenamiento y Windows Server 2025 proporciona los servicios de directorio mediante Active Directory.

Finalmente, se incorporan dos equipos cliente, Windows 11 Pro y Debian 13, para comprobar la conectividad y el funcionamiento de los servicios desplegados.
