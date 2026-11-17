# 09 — Registro de incidencias y contingencia

Durante la instalación y configuración de los diferentes equipos de la infraestructura se produjeron algunas incidencias de red y configuración. A continuación, se detallan los problemas encontrados y su resolución.

| Equipo | Incidencia encontrada | Solución / Resultado |
|---|---|---|
| MikroTik | No proporcionaba conexión de red a los clientes. | Se revisó la configuración de red y DHCP hasta conseguir conectividad. |
| Proxmox | No estaba conectado a la red interna y no recibía ni respondía a los paquetes ping porque utilizaba un adaptador NAT. | Se tuvo que cambiar la configuración de red para integrarlo en la red interna. |
| Windows Server | No se encontraron errores durante la instalación ni durante la creación del dominio. | Configuración completada correctamente. |
| Debian con nftables | No tenía conectividad con el MikroTik porque la dirección IP no estaba configurada correctamente. | Se configuró la dirección IP correspondiente a la red `192.168.25.0/24`. |
| OPNsense | No se encontraron errores durante su instalación y configuración. | Configuración completada correctamente. |
| Clientes Debian y Windows 11 Pro | No se encontraron problemas de conectividad ni configuración. | Ambos clientes funcionaron correctamente dentro de la red. |

### Conclusión

Durante el desarrollo del proyecto, las principales dificultades estuvieron relacionadas con la configuración de red de MikroTik, Proxmox y Debian. Estos problemas se solucionaron revisando los adaptadores de red, las direcciones IP y la configuración de conectividad.

Por otro lado, Windows Server, OPNsense y los equipos cliente Debian y Windows 11 Pro funcionaron correctamente, sin presentar incidencias importantes.

Estas pruebas permitieron identificar y solucionar errores de configuración, consiguiendo finalmente una infraestructura funcional dentro de la red empresarial `192.168.25.0/24`.
