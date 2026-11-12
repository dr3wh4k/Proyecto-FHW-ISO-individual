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
- Windows: equipo cliente para realizar pruebas.
- VirtualBox: entorno de virtualización del laboratorio.

## 3. Direccionamiento IP

La red principal del laboratorio utiliza el segmento `192.168.25.0/24`.

| Dispositivo | Interfaz | Dirección IP |
|---|---|---|
| MikroTik CHR | ether2 (LAN) | `192.168.25.1/24` |
| MikroTik CHR | ether3 (WAN) | Red exterior |
| OPNsense | em0 (WAN) | `192.168.25.249` (DHCP) |
| OPNsense | em1 (LAN) | Pendiente de confirmar |
| Debian | enp0s3 | DHCP |
| TrueNAS | Gestión | DHCP |
| TrueNAS | Gestión futura | `192.168.25.200` (propuesta) |
| Proxmox Nodo 1 | Gestión | Pendiente |
| Proxmox Nodo 2 | Gestión | Pendiente |
| Proxmox Nodo 3 | Gestión | Pendiente |
| Windows Server | Red LAN | Pendiente |
| Cliente Windows | Red LAN | Pendiente |

Las direcciones de los nodos Proxmox y de los equipos Windows se definirán posteriormente.

## 4. Índice de documentación

| Documento | Descripción |
|---|---|
| [00 - Predicciones](docs/00-predicciones.md) | Hipótesis iniciales y riesgos |
| [01 - Análisis de necesidades](docs/01-analisis-necesidades.md) | Requisitos de la infraestructura |
| [02 - Inventario de recursos](docs/02-inventario-recursos.md) | Hardware y software |
| [03 - Diseño de red](docs/03-diseno-red.md) | Topología y direccionamiento IP |
| [04 - Servicios de directorio](docs/04-diseno-servicios-directorio.md) | Diseño de servicios de directorio |
| [05 - Instalación](docs/05-instalacion.md) | Instalación de los sistemas |
| [06 - Configuración](docs/06-configuracion-sistemas-servicios.md) | Configuración de sistemas y servicios |
| [07 - Almacenamiento](docs/07-almacenamiento-comparticion.md) | Almacenamiento y compartición |
| [08 - Seguridad](docs/08-seguridad-administracion.md) | Seguridad y administración |
| [09 - Pruebas](docs/09-pruebas-verificacion.md) | Verificación de funcionamiento |
| [10 - Conclusiones](docs/10-conclusiones.md) | Evaluación final |

## 5. Estructura del repositorio

- `docs/`: documentación técnica del proyecto.
- `diagramas/`: esquemas y topología de red.
- `evidencias/`: capturas de pantalla y pruebas realizadas.

## 6. Estado del proyecto

El proyecto se encuentra en fase de despliegue y configuración.

Las direcciones IP y servicios se documentarán diferenciando entre configuraciones realizadas, propuestas y tareas pendientes.

## 7. Criterios de documentación

- No se considerará configurado ningún servicio hasta comprobar su funcionamiento.
- Las direcciones IP pendientes se definirán antes de completar la configuración.
- Las pruebas se acompañarán de evidencias.
- Se documentarán las incidencias y sus soluciones.
