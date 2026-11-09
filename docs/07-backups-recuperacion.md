# 07 — Copias de seguridad y recuperación

## Política
| Elemento | Qué se copia | Frecuencia | Destino | Retención |
|---|---|---|---|---|
| OPNsense | Exportación de configuración | Tras cambios | TrueNAS/medio independiente | PENDIENTE |
| Proxmox | Configuración y backups de VM/CT | PENDIENTE | TrueNAS/medio independiente | PENDIENTE |
| Windows Server | Estado del sistema/datos necesarios | PENDIENTE | Destino independiente | PENDIENTE |
| GNU/Linux | Configuración y datos de servicios | PENDIENTE | Destino independiente | PENDIENTE |
| TrueNAS | Configuración y datos críticos | PENDIENTE | Destino independiente | PENDIENTE |

## Objetivos
- RPO objetivo:
- RTO objetivo:
- Justificación:

## Prueba de restauración
1. Identificar la copia y su fecha.
2. Confirmar que el destino de restauración no sobrescribirá datos necesarios.
3. Restaurar una VM/archivo de prueba.
4. Comprobar arranque, servicio, permisos y contenido.
5. Registrar tiempo real y posibles pérdidas.

| Elemento restaurado | Backup utilizado | Tiempo | Datos recuperados | Resultado |
|---|---|---:|---|---|
| PENDIENTE | PENDIENTE | PENDIENTE | PENDIENTE | PENDIENTE |

Un snapshot no es una copia independiente. RAID/ZFS no sustituye a backups externos.
