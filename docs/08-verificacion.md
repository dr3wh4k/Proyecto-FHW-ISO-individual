# 08 — Verificación y monitorización

## Matriz de pruebas
| ID | Prueba | Procedimiento | Resultado esperado | Resultado real | Evidencia |
|---|---|---|---|---|---|
| V01 | Gateway LAN | `ping 192.168.25.1` | Respuesta | PENDIENTE | |
| V02 | Gestión Proxmox | HTTPS a `https://192.168.25.10:8006` desde LAN autorizada | Login disponible | PENDIENTE | |
| V03 | TrueNAS | HTTPS a `https://192.168.25.20` | Login disponible | PENDIENTE | |
| V04 | DNS | `nslookup`/`dig` | Resolución esperada | PENDIENTE | |
| V05 | NAT/salida | `curl` a destino permitido | Conexión correcta | PENDIENTE | |
| V06 | Filtrado | Intento controlado de conexión no permitida | Bloqueo y log | PENDIENTE | |
| V07 | SMB/NFS | Crear y leer archivo según permisos | Acceso correcto | PENDIENTE | |
| V08 | Backup/restore | Restaurar VM o archivo de prueba | Servicio/dato recuperado | PENDIENTE | |

## Monitorización
- Herramienta:
- Recursos observados: CPU, RAM, disco, red y servicios.
- Umbrales:
- Carga simulada:
- Resultado antes/después:
- Optimización aplicada:
