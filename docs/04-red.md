# 04 — Diseño de red

## Plan IPv4

Red LAN: `192.168.25.0/24`  
Máscara: `255.255.255.0`  
Gateway LAN: `192.168.25.1`  
Broadcast: `192.168.25.255`

| Dispositivo | Interfaz | IP/prefijo | Gateway | DNS | Método |
|---|---|---|---|---|---|
| OPNsense | WAN | PENDIENTE profesor | PENDIENTE | PENDIENTE | Según profesor |
| OPNsense | LAN | `192.168.25.1/24` | — | PENDIENTE | Estática |
| Proxmox | Gestión | `192.168.25.10/24` | `.1` | `.1`/PENDIENTE | Estática |
| TrueNAS | Gestión | `192.168.25.20/24` | `.1` | `.1`/PENDIENTE | Estática |
| Windows Server | LAN | `192.168.25.30/24` | `.1` | Según rol DNS | Estática |
| GNU/Linux | LAN | `192.168.25.40/24` | `.1` | PENDIENTE | Estática |
| Cliente Dirección | LAN | `192.168.25.101/24` | `.1` | DHCP/DNS | PENDIENTE |
| Cliente Administración | LAN | `192.168.25.102/24` | `.1` | DHCP/DNS | PENDIENTE |
| Cliente Comercial | LAN | `192.168.25.103/24` | `.1` | DHCP/DNS | PENDIENTE |
| Cliente Producción | LAN | `192.168.25.104/24` | `.1` | DHCP/DNS | PENDIENTE |
| Cliente Informática | LAN | `192.168.25.105/24` | `.1` | DHCP/DNS | PENDIENTE |

## DHCP
Si OPNsense ofrece DHCP, rango propuesto: `192.168.25.100–192.168.25.199`. Configurar exclusiones/reservas para que no se solape con direcciones estáticas. No activar DHCP en la WAN ni en el segmento compartido del aula.

## Interfaces y recorrido del tráfico
Describir físicamente cada NIC y virtualmente cada bridge de Proxmox:
- WAN OPNsense → red exterior autorizada:
- LAN OPNsense → switch/red interna:
- Proxmox management → LAN:
- TrueNAS → LAN:
- VM/CT → bridge correspondiente:

## Comprobaciones
| Origen | Destino | Prueba | Resultado esperado | Resultado real |
|---|---|---|---|---|
| Cliente | Gateway `.1` | `ping 192.168.25.1` | Responde | PENDIENTE |
| Cliente | Proxmox `.10` | `ping 192.168.25.10` | Responde si permitido | PENDIENTE |
| Cliente | TrueNAS `.20` | `ping 192.168.25.20` | Responde si permitido | PENDIENTE |
| Cliente | Exterior | `ping`/`curl` autorizado | Según reglas y DNS | PENDIENTE |
| WAN | Administración LAN | Prueba controlada | Bloqueado | PENDIENTE |

## Configuración real de cada interfaz
Añadir salidas anonimizadas de `ip a`, `ip route`, `ipconfig /all` o capturas de OPNsense. No publicar MAC si no es necesario ni credenciales.
