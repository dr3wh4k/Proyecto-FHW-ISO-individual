# Diagrama lógico

flowchart TB
    VB["ORACLE VIRTUALBOX<br/>Entorno de virtualización"]

    subgraph RED["RED INTERNA — 192.168.25.0/24"]
        direction TB

        MT["MIKROTIK CHR<br/>Router principal<br/>192.168.25.1<br/>DHCP · NAT · Routing"]

        subgraph VIRT["CLÚSTER DE VIRTUALIZACIÓN"]
            direction LR
            P1["Proxmox Node 1<br/>192.168.25.11"]
            P2["Proxmox Node 2<br/>192.168.25.12"]
            P3["Proxmox Node 3<br/>192.168.25.13"]
            P1 <-->|Cluster| P2
            P2 <-->|Cluster| P3
            P1 <-->|Cluster| P3
        end

        subgraph COM["SERVIDORES DE COMUNICACIONES Y SEGURIDAD"]
            direction LR
            FW["OPNsense<br/>WAN: 192.168.25.248<br/>LAN: em1<br/>Firewall"]
            NFT["Debian Server<br/>192.168.25.40<br/>nftables"]
        end

        subgraph SERV["SERVIDORES DE INFRAESTRUCTURA"]
            direction LR
            WS["Windows Server 2025<br/>192.168.25.14<br/>Active Directory · DNS"]
            NAS["TrueNAS<br/>192.168.25.247<br/>Almacenamiento · RAID"]
        end

        subgraph CLIENTES["EQUIPOS CLIENTE"]
            direction LR
            WC["Windows 11 Pro<br/>Windows-cli<br/>DHCP"]
            DC["Debian 13<br/>Debian-cli<br/>DHCP"]
        end

        MT --- P1
        MT --- P2
        MT --- P3
        MT --- FW
        MT --- NFT
        MT --- WS
        MT --- NAS
        MT --- WC
        MT --- DC
    end

    VB --> RED

    classDef router fill:#8b5cf6,color:#fff,stroke:#6d28d9
    classDef virtualization fill:#2563eb,color:#fff,stroke:#1d4ed8
    classDef security fill:#dc2626,color:#fff,stroke:#991b1b
    classDef server fill:#0f766e,color:#fff,stroke:#115e59
    classDef client fill:#475569,color:#fff,stroke:#334155

    class MT router
    class P1,P2,P3 virtualization
    class FW,NFT security
    class WS,NAS server
    class WC,DC client



### Arquitectura de la infraestructura

La infraestructura del proyecto ISO-FHW está desplegada mediante Oracle VirtualBox, utilizando una red interna con direccionamiento `192.168.25.0/24`.

El MikroTik CHR actúa como router principal, proporcionando conectividad y asignación automática de direcciones IP mediante DHCP.

La infraestructura incorpora tres nodos Proxmox VE que forman un clúster de virtualización, junto con diferentes servidores especializados en comunicaciones, seguridad, almacenamiento y administración de usuarios.

OPNsense y Debian con nftables proporcionan funcionalidades de seguridad y filtrado de tráfico. TrueNAS centraliza el almacenamiento y Windows Server 2025 proporciona los servicios de directorio mediante Active Directory.

Finalmente, se incorporan dos equipos cliente, Windows 11 Pro y Debian 13, para comprobar la conectividad y el funcionamiento de los servicios desplegados.
