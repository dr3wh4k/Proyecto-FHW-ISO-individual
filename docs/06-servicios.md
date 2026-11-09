# 06 — Máquinas virtuales y servicios

## Inventario de VM/CT
| ID | Nombre | SO | Rol | vCPU | RAM | Disco | Bridge | IP |
|---:|---|---|---|---:|---:|---:|---|---|
| 100 | fw01 | OPNsense | Firewall/router | PEND. | PEND. | PEND. | WAN+LAN | `.1` LAN |
| 101 | nas01 | TrueNAS | NAS | PEND. | PEND. | PEND. | LAN | `.20` |
| 102 | dc01 | Windows Server 2025 | AD DS/DNS | PEND. | PEND. | PEND. | LAN | `.30` |
| 103 | srv01 | Debian | Servicios | PEND. | PEND. | PEND. | LAN | `.40` |

## Recursos del host
- CPU total:
- RAM total:
- Espacio disponible:
- RAM reservada para Proxmox:
- Consumo simultáneo medido:
- VM máximas ejecutables sin degradación:

## Contenedores frente a máquinas virtuales
Explicar que una VM virtualiza hardware y ejecuta su propio kernel/sistema operativo; un contenedor comparte el kernel del host y aísla procesos/recursos. Justificar según compatibilidad, aislamiento y consumo.

## Clúster
- Número de nodos disponibles:
- ¿Clúster desplegado o solo diseñado?:
- Quorum:
- Red de clúster:
- Almacenamiento:
- Migración probada:
- Limitaciones:

No afirmar HA si no se han configurado y probado los componentes necesarios.
