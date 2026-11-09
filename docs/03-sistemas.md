# Servidores de comunicaciones

## 1. Introducción

La infraestructura de red de la empresa dispone de tres servidores de comunicaciones encargados de gestionar, controlar y proteger el tráfico de red. Cada uno desempeña una función específica dentro de la infraestructura.

Los tres servidores utilizados son:

- **MikroTik:** enrutamiento y gestión del tráfico de red.
- **OPNsense:** seguridad perimetral y filtrado del tráfico mediante firewall.
- **Debian con nftables:** cortafuegos basado en Linux para controlar las comunicaciones de red.

## 2. MikroTik

### Función principal

MikroTik se utiliza como dispositivo de enrutamiento para gestionar las comunicaciones entre diferentes redes y permitir el intercambio de tráfico.

### Funciones

- Enrutamiento entre redes.
- Gestión de interfaces de red.
- Configuración de direcciones IP.
- Administración de rutas.
- Control del tráfico de red.

### Direccionamiento IP

| Parámetro | Configuración |
|---|---|
| Dirección IP | `192.168.25.1` |
| Máscara | `/24` |
| Sistema | MikroTik RouterOS / CHR |

## 3. OPNsense

### Función principal

OPNsense se utiliza como servidor de seguridad perimetral, encargado de controlar y filtrar las comunicaciones mediante reglas de firewall.

### Funciones

- Filtrado de tráfico entrante y saliente.
- Configuración de reglas de firewall.
- Control de conexiones entre redes.
- Gestión de interfaces de red.
- Protección de la infraestructura frente a conexiones no autorizadas.

### Direccionamiento IP

| Parámetro | Configuración |
|---|---|
| Dirección IP | `192.168.25.2` |
| Sistema | OPNsense |

## 4. Debian con nftables

### Función principal

Debian actúa como servidor de comunicaciones mediante el uso de `nftables`, una herramienta del sistema Linux que permite configurar y administrar reglas de filtrado de paquetes.

### Funciones

- Filtrado de paquetes de red.
- Control de conexiones entrantes.
- Control de conexiones salientes.
- Gestión del tráfico reenviado entre interfaces.
- Aplicación de políticas de seguridad.
- Protección de los servicios de red.

### Tecnología utilizada

| Parámetro | Configuración |
|---|---|
| Sistema operativo | Debian GNU/Linux |
| Firewall | nftables |
| Gestión de reglas | `nft` |
| Configuración | `/etc/nftables.conf` |

### Políticas de seguridad

La configuración del firewall contempla las siguientes políticas:

- Aceptar el tráfico de la interfaz local (`loopback`).
- Permitir conexiones establecidas y relacionadas.
- Controlar el tráfico ICMP.
- Bloquear conexiones no autorizadas.
- Definir políticas específicas para el tráfico reenviado.
- Permitir las comunicaciones necesarias para el funcionamiento de la infraestructura.

## 5. Resumen de los servidores de comunicaciones

| Servidor | Tecnología | Responsabilidad |
|---|---|---|
| MikroTik | RouterOS / CHR | Enrutamiento |
| OPNsense | OPNsense | Seguridad perimetral y firewall |
| Debian | nftables | Filtrado de paquetes y control del tráfico |

## 6. Conclusión

La infraestructura incorpora tres servidores de comunicaciones con responsabilidades diferenciadas. MikroTik se encarga del enrutamiento, OPNsense proporciona seguridad perimetral y Debian utiliza nftables para aplicar políticas de filtrado de tráfico.

La combinación de estas tecnologías permite implementar una infraestructura de red segmentada, administrable y con diferentes capas de seguridad.

