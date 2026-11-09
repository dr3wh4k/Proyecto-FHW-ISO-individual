# 05 — Instalación de la plataforma

En este apartado se documenta el proceso de instalación, configuración inicial y puesta en funcionamiento de los sistemas que forman parte de la infraestructura informática de la empresa.

Se incluyen los requisitos de hardware, las versiones utilizadas, la configuración de red, el almacenamiento, las medidas de seguridad y las pruebas realizadas.

---

## 5.1 — Proxmox VE

### Información general

- **Sistema:** Proxmox Virtual Environment (Proxmox VE).
- **ISO y versión:** 
- **Fuente oficial:** https://www.proxmox.com/en/downloads
- **Verificación de integridad:** comprobar el checksum SHA-256 de la ISO descargada.
- **Tipo de instalación:** equipo físico / máquina virtual.
- **Objetivo:** proporcionar una plataforma centralizada para crear, ejecutar y administrar máquinas virtuales y contenedores.

### Requisitos y hardware

- **Procesador:**
- **Memoria RAM:**
- **Almacenamiento disponible:**
- **Virtualización:** Intel VT-x / AMD-V.
- **Virtualización anidada:** activada si Proxmox se ejecuta dentro de VirtualBox.
- **Adaptadores de red:**


### Configuración de red

| Parámetro | Configuración |
|---|---|
| Dirección IP | `192.168.25.10/24` |
| Gateway | `192.168.25.1` |
### Almacenamiento

- **Almacenamiento local:** `local`.
- **Almacenamiento de discos virtuales:** `local-lvm` o el almacenamiento configurado durante la instalación.

### Configuración posterior a la instalación

- Acceso al panel web de administración mediante HTTPS.
- Comprobación del estado de los servicios de Proxmox.
- Configuración de repositorios de actualizaciones.
- Instalación de actualizaciones disponibles.
- Comprobación de conectividad de red.
- Configuración de almacenamiento para máquinas virtuales.
- Creación de máquinas virtuales y contenedores.

### Comprobaciones

- [ ] Acceso al panel web de Proxmox.
- [ ] Acceso mediante SSH.
- [ ] Conectividad con el gateway.
- [ ] Resolución DNS.
- [ ] Detección correcta de los discos.
- [ ] Creación y arranque de una máquina virtual.
- [ ] Comprobación de las actualizaciones.


---

## 5.2 — OPNsense

### Información general

- **Sistema:** OPNsense.
- **ISO/versión:**
- **Fuente oficial:** https://opnsense.org/download/
- **Tipo:** equipo físico / máquina virtual.
- **Objetivo:** proporcionar seguridad perimetral mediante un firewall, controlar las comunicaciones entre redes y aplicar políticas de filtrado de tráfico.

### Requisitos y hardware

- **Procesador:**
- **Memoria RAM:**
- **Disco virtual o físico:**
- **Adaptadores de red necesarios:** mínimo dos interfaces, WAN y LAN.
- **Hipervisor:** Proxmox / VirtualBox / instalación física.


### Configuración de interfaces

| Parámetro | Configuración |
|---|---|
| Interfaz WAN | |
| Interfaz LAN | |
| Dirección WAN | Asignada por el profesor |
| Dirección LAN | `192.168.25.1/24` |
| Gateway WAN | |
| DNS | |

### Configuración de servicios

- **DHCP:** activado / desactivado.
- **DNS:** configuración de resolución de nombres.
- **NAT:** configuración de traducción de direcciones de red.
- **Firewall:** reglas de entrada, salida y comunicación entre redes.
- **Acceso administrativo:** interfaz web HTTPS.

### Reglas de firewall

Se configurarán reglas para permitir únicamente las comunicaciones necesarias para el funcionamiento de la infraestructura.

| Regla | Origen | Destino | Puerto/protocolo | Acción |
|---|---|---|---|---|
| Administración | | | HTTPS | Permitir |
| DNS | | | TCP/UDP 53 | Permitir |
| DHCP | | | UDP 67/68 | Según configuración |
| ICMP | | | ICMP | Según configuración |
| Tráfico no autorizado | | | Cualquiera | Bloquear |

### NAT y enrutamiento

- Configuración del tipo de NAT.
- Comprobación de la salida hacia Internet.
- Configuración de rutas necesarias.
- Comprobación de la comunicación entre interfaces.
- Verificación de que las reglas de firewall se aplican correctamente.

### Seguridad y mantenimiento

- Cambio de credenciales predeterminadas.
- Actualización del sistema.
- Restricción del acceso al panel de administración.
- Copia de seguridad de la configuración.
- Revisión de registros y eventos del firewall.

### Comprobaciones

- [ ] Interfaces WAN y LAN detectadas.
- [ ] Dirección IP correctamente asignada.
- [ ] Acceso al panel web.
- [ ] Conectividad con el gateway correspondiente.
- [ ] Funcionamiento del NAT.
- [ ] Reglas de firewall aplicadas.
- [ ] DHCP funcionando, si está activado.
- [ ] Copia de seguridad de la configuración realizada.


---

## 5.3 — TrueNAS

### Información general

- **Sistema:** TrueNAS.
- **Edición/versión:** TrueNAS SCALE / TrueNAS Community Edition / otra.
- **Fuente oficial:** https://www.truenas.com/download-truenas-community-edition/
- **Tipo:** equipo físico / máquina virtual.
- **Objetivo:** proporcionar almacenamiento centralizado para la empresa, permitiendo gestionar discos, conjuntos de datos, usuarios y recursos compartidos.

### Requisitos y hardware

- **Procesador:**
- **Memoria RAM:**
- **Disco de arranque:**
- **Discos destinados al almacenamiento:**
- **Controladora de almacenamiento:**
- **Adaptador de red:**

### Configuración de instalación

- **ISO utilizada:**
- **Disco de instalación:**
- **Método de instalación:**
- **Usuario administrador:**
- **Contraseña:**
- **Hostname:**

### Configuración de red

| Parámetro | Configuración |
|---|---|
| Dirección IP | `192.168.25.20/24` |
| Gateway | |
| DNS | |
| Interfaz de red | |
| Hostname | |

### Gestión del almacenamiento

- **Discos identificados:**
- **Capacidad de cada disco:**
- **Capacidad total:**
- **Pool de almacenamiento:**
- **Tipo de RAID o configuración:** 
- **Datasets creados:**

Se documentará la organización del almacenamiento mediante pools y datasets, indicando la finalidad de cada uno.

| Dataset | Finalidad | Permisos |
|---|---|---|
| `empresa` | Almacenamiento general | |
| `departamentos` | Documentos de los departamentos | |
| `copias_seguridad` | Almacenamiento de backups | |

### Usuarios y grupos

- Creación de usuarios.
- Creación de grupos.
- Asignación de permisos.
- Restricción del acceso a los datasets.
- Comprobación de los permisos de lectura y escritura.

| Usuario/grupo | Recurso | Permisos |
|---|---|---|
| Administradores | Todos los recursos necesarios | Administración |
| Usuarios | Documentos compartidos | Lectura/escritura según necesidad |

### Servicios de compartición

- **SMB:** compartir carpetas con equipos Windows.
- **NFS:** compartir directorios con sistemas Linux, si se necesita.
- **Servicio SMB:** activado / desactivado.
- **Servicio NFS:** activado / desactivado.
- **Permisos de acceso:** configurados según usuarios y grupos.

### Seguridad y mantenimiento

- Configuración de permisos.
- Protección del acceso administrativo.
- Comprobación del estado de los discos.
- Configuración de alertas.
- Copia de seguridad de la configuración.
- Planificación de copias de seguridad de los datos.

### Comprobaciones

- [ ] Acceso al panel web.
- [ ] Detección de todos los discos.
- [ ] Pool de almacenamiento creado.
- [ ] Datasets creados.
- [ ] Usuarios y grupos configurados.
- [ ] Permisos comprobados.
- [ ] Servicio SMB/NFS operativo.
- [ ] Acceso desde un cliente Windows o Linux.
- [ ] Copia de seguridad de la configuración realizada.

### Evidencias

- [ ] Pantalla de instalación.
- [ ] Información de la versión.
- [ ] Configuración IP.
- [ ] Panel web de TrueNAS.
- [ ] Discos detectados.
- [ ] Pool y datasets.
- [ ] Usuarios y grupos.
- [ ] Configuración SMB/NFS.
- [ ] Prueba de acceso desde un cliente.
- [ ] Copia de seguridad.

---

## 5.4 — Debian con nftables

### Información general

- **Sistema:** Debian GNU/Linux.
- **Versión:**
- **Fuente oficial:** https://www.debian.org/distrib/
- **Tipo:** máquina virtual / equipo físico.
- **Objetivo:** implementar un servidor de comunicaciones con funciones de cortafuegos mediante nftables, controlando el tráfico entrante, saliente y reenviado.

### Requisitos y hardware

- **Procesador:**
- **Memoria RAM:**
- **Disco:**
- **Adaptadores de red:**
- **Interfaz de red interna:**
- **Interfaz de red externa:**

### Configuración de instalación

- **ISO utilizada:**
- **Método de instalación:**
- **Entorno gráfico:** instalado / no instalado.
- **Hostname:**
- **Usuario administrador:**
- **Acceso SSH:** activado / desactivado.

### Configuración de red

| Parámetro | Configuración |
|---|---|
| Dirección IP | |
| Máscara | |
| Gateway | |
| DNS | |
| Interfaz interna | |
| Interfaz externa | |

### Configuración de nftables

- Instalación del paquete `nftables`.
- Habilitación del servicio.
- Configuración del archivo `/etc/nftables.conf`.
- Creación de tablas y cadenas.
- Definición de políticas de entrada, salida y reenvío.
- Configuración de reglas para permitir tráfico autorizado.
- Bloqueo del tráfico no permitido.

### Políticas de seguridad

- Permitir el tráfico de loopback.
- Permitir conexiones establecidas y relacionadas.
- Controlar el tráfico ICMP.
- Permitir SSH únicamente desde los equipos autorizados.
- Bloquear conexiones no autorizadas.
- Definir las reglas necesarias para el tráfico reenviado.
- Mantener una política de filtrado coherente con la topología de red.

### Comandos de administración

| Comando | Función |
|---|---|
| `sudo nft list ruleset` | Mostrar todas las reglas activas |
| `sudo nft list tables` | Mostrar las tablas existentes |
| `sudo nft -f /etc/nftables.conf` | Cargar la configuración |
| `sudo systemctl status nftables` | Consultar el estado del servicio |
| `sudo systemctl enable nftables` | Habilitar el servicio al arrancar |
| `sudo systemctl restart nftables` | Reiniciar el servicio |

### Comprobaciones

- [ ] Debian instalado correctamente.
- [ ] Interfaces de red detectadas.
- [ ] Direccionamiento IP configurado.
- [ ] Conectividad comprobada.
- [ ] nftables instalado.
- [ ] Reglas cargadas correctamente.
- [ ] Servicio nftables habilitado.
- [ ] Tráfico autorizado permitido.
- [ ] Tráfico no autorizado bloqueado.
- [ ] Reglas persistentes tras reiniciar.

### Evidencias

- [ ] Pantalla de instalación.
- [ ] Versión de Debian.
- [ ] Configuración de interfaces.
- [ ] Archivo `/etc/nftables.conf`.
- [ ] Resultado de `nft list ruleset`.
- [ ] Estado del servicio nftables.
- [ ] Pruebas de conectividad.
- [ ] Pruebas de filtrado.

---

## 5.5 — Consideraciones de integración de la infraestructura

Una vez instalados los sistemas, se comprobará que todos los equipos pueden comunicarse de acuerdo con el diseño de red establecido.

### Comprobaciones generales

- [ ] Todos los sistemas arrancan correctamente.
- [ ] Las direcciones IP no están duplicadas.
- [ ] Las máscaras de red son correctas.
- [ ] Los gateways están configurados correctamente.
- [ ] La resolución DNS funciona.
- [ ] Las rutas entre redes son correctas.
- [ ] Los servicios de red están activos.
- [ ] Las reglas de firewall no bloquean comunicaciones necesarias.
- [ ] Los sistemas están actualizados.
- [ ] Se han realizado copias de seguridad de las configuraciones.


### Conclusión

La instalación de Proxmox VE, OPNsense, TrueNAS y Debian permite disponer de una infraestructura virtualizada, con almacenamiento centralizado y diferentes capas de control de las comunicaciones.

Cada sistema desempeña una función dentro de la infraestructura y su configuración se documenta mediante parámetros técnicos, comprobaciones y evidencias de funcionamiento.
