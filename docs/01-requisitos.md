# 01 — Requisitos y necesidades


## Necesidades técnicas
| Necesidad | Requisito | Prioridad | Cómo se comprobará |
|---|---|---|---|
| Conectividad LAN/WAN | Comunicación controlada entre LAN y exterior | Alta | Ping, traceroute y reglas |
| Virtualización | Alojar servidores de prueba | Alta | VM arrancan y servicios responden |
| Almacenamiento | Compartir y proteger datos | Alta | SMB/NFS, permisos y restauración |
| Identidad | Gestión centralizada si se implanta AD DS | Media | Inicio de sesión y DNS |
| Copias | Recuperar sistemas/datos críticos | Alta | Restauración real |
| Monitorización | Detectar consumo y eventos | Media | Registros y alertas |

## Restricciones
- LAN asignada para este documento: `192.168.25.0/24`.
- WAN: red compartida del aula `172.16.222.0/24`, dirección concreta asignada por el profesor.
- Recursos físicos: PENDIENTE de inventario.
- Presupuesto/licencias: PENDIENTE.
