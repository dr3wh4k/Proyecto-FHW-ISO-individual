# 01 — Análisis de necesidades

## 1. Introducción

El objetivo de este documento es identificar las necesidades técnicas y funcionales de la infraestructura informática que se va a desplegar.

Se plantea un entorno de laboratorio que simula una infraestructura empresarial mediante máquinas virtuales y diferentes servicios de red.

## 2. Necesidades funcionales

La infraestructura deberá permitir:

- Administrar máquinas virtuales mediante Proxmox VE.
- Gestionar tres nodos dentro de un entorno de virtualización.
- Proporcionar conectividad mediante MikroTik CHR.
- Asignar direcciones IP automáticamente mediante DHCP.
- Filtrar y controlar el tráfico mediante OPNsense.
- Aplicar reglas de firewall en Debian utilizando nftables.
- Disponer de almacenamiento centralizado mediante TrueNAS.
- Instalar y configurar Windows Server.
- Conectar un cliente Windows para realizar pruebas.
- Comprobar la comunicación entre los diferentes equipos.

## 3. Necesidades no funcionales

| Necesidad | Descripción |
|---|---|
| Seguridad | Controlar el tráfico entre redes y sistemas. |
| Disponibilidad | Mantener los servicios accesibles durante las pruebas. |
| Escalabilidad | Permitir añadir nuevos equipos y servicios. |
| Administración | Facilitar la gestión centralizada. |
| Organización | Mantener documentadas las configuraciones. |
| Rendimiento | Distribuir adecuadamente los recursos disponibles. |

## 4. Recursos necesarios

### Hardware

- Ordenador físico capaz de ejecutar VirtualBox.
- Memoria RAM suficiente para las máquinas virtuales.
- Espacio de almacenamiento para discos virtuales.
- Procesador compatible con virtualización.

### Software

- Oracle VirtualBox.
- Proxmox VE.
- MikroTik CHR.
- OPNsense.
- Debian.
- TrueNAS.
- Windows Server.
- Windows cliente.

## 5. Servicios previstos

| Servicio | Sistema responsable |
|---|---|
| Enrutamiento | MikroTik CHR |
| DHCP de la red principal | MikroTik CHR |
| Firewall de red | OPNsense |
| Firewall Linux | Debian con nftables |
| Virtualización | Proxmox VE |
| Almacenamiento | TrueNAS |
| Servicios de servidor | Windows Server |
| Equipo de pruebas | Cliente Windows |

## 6. Resultado esperado

La infraestructura deberá permitir comprobar el funcionamiento conjunto de los sistemas, la conectividad entre redes y la aplicación de medidas de seguridad.
