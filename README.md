# Proyecto ISO-FHW — Infraestructura de red y sistemas

## 1. Descripción del proyecto

Este proyecto tiene como objetivo diseñar, desplegar, configurar y documentar una infraestructura informática empresarial mediante máquinas virtuales y servicios de red.

La infraestructura incluye sistemas de virtualización, almacenamiento, comunicaciones, cortafuegos y equipos cliente.

El laboratorio se desarrolla utilizando VirtualBox y diferentes sistemas operativos y plataformas de administración.

## 2. Tecnologías utilizadas

- Proxmox VE: plataforma de virtualización y gestión de nodos.
- MikroTik CHR: router principal y servidor DHCP.
- OPNsense: cortafuegos y servidor de comunicaciones.
- Debian: sistema Linux con configuración de red y firewall mediante nftables.
- TrueNAS: almacenamiento centralizado.
- Windows Server: servidor de infraestructura y servicios.
- Windows y Debian: equipos clientes para realizar pruebas.
- VirtualBox: entorno de virtualización del laboratorio.

## 3. Direccionamiento IP

La red principal del laboratorio utiliza el segmento `192.168.25.0/24`.

| Dispositivo | Interfaz | Dirección IP |
|---|---|---|
| MikroTik CHR | ether2 (LAN) | `192.168.25.1/24` |
| MikroTik CHR | ether3 (WAN) | Red exterior |
| OPNsense | em0 (WAN) | `192.168.25.2` |
| Debian NFTABLES | enp0s3 | `192.168.25.40` |
| TrueNAS | Gestión futura | `192.168.25.247` |
| Proxmox Nodo 1 | Gestión | `192.168.25.11` |
| Proxmox Nodo 2 | Gestión | `192.168.25.12` |
| Proxmox Nodo 3 | Gestión | `192.168.25.13` |
| Windows Server | Red LAN | `192.168.25.14` |
| Cliente Windows | Red LAN | DHCP |
| Cliente Debian | Red LAN | DHCP |

## 4. Índice de documentación

Toda la documentación del proyecto está organizada en el directorio [`docs/`](docs/).

| Nº | Documento | Descripción |
|---|---|---|
| 00 | [Predicciones](docs/00-predicciones.md) | Estimación inicial de los recursos y necesidades del proyecto. |
| 01 | [Análisis de necesidades](docs/01-analisis-necesidades.md) | Identificación de los requisitos técnicos y funcionales de la infraestructura. |
| 02 | [Inventario de recursos](docs/02-inventario-recursos.md) | Inventario del hardware, software y recursos disponibles. |
| 03 | [Diseño de red](docs/03-diseño-red.md) | Topología, direccionamiento IP y arquitectura de red. |
| 04 | [Diseño de servicios de directorio](docs/04-diseño-servicios-directorio.md) | Planificación de Active Directory y servicios de directorio. |
| 05 | [Instalación de la plataforma](docs/05-instalacion.md) | Instalación y configuración de los sistemas y servidores virtualizados. |
| 06 | [Servicios](docs/06-servicios.md) | Configuración y puesta en marcha de los servicios de infraestructura. |
| 07 | [Backups y recuperación](docs/07-backups-recuperacion.md) | Estrategias de copias de seguridad y procedimientos de recuperación. |
| 08 | [Análisis y optimización](docs/08-analisis-optimizacion.md) | Evaluación del rendimiento y optimización de los recursos. |
| 09 | [Registro de incidencias](docs/09-incidencias.md) | Problemas encontrados durante el proyecto y soluciones aplicadas. |
| 10 | [Conclusiones](docs/10-conclusiones.md) | Valoración final, resultados obtenidos y posibles mejoras.

## 5. Estructura del repositorio

- `docs/`: documentación técnica del proyecto.
- `diagramas/`: esquemas y topología de red.
- `evidencias/`: capturas de pantalla y pruebas realizadas.

## 6. Estado del proyecto

Las direcciones IP y servicios se documentarán diferenciando entre configuraciones realizadas, propuestas y tareas pendientes.

## 7. Criterios de documentación

- No se considerará configurado ningún servicio hasta comprobar su funcionamiento.
- Las direcciones IP, junto al esquema de red se definirán antes de completar la configuración.
- Las pruebas se acompañarán de evidencias.
- Se documentarán las incidencias y sus soluciones.
