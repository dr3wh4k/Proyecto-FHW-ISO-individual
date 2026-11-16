# 07 — Análisis y optimización de recursos de virtualización

## 1. Análisis de los recursos del equipo físico

El objetivo de esta práctica es analizar los recursos del ordenador físico y comprobar cómo afecta la ejecución simultánea de las máquinas virtuales del proyecto ISO-FHW.

### 1.1. Características del equipo físico

Para realizar el proyecto se utiliza un ordenador doméstico con las siguientes características:

| **Recurso** | **Características** |
|---|---|
| Procesador | Intel Core i7 |
| Memoria RAM | 16 GB |
| Almacenamiento | Disco externo SanDisk de 1 TB |
| Software de virtualización | Oracle VirtualBox |
| Sistema operativo anfitrión | Windows |

### 1.2. Análisis de las máquinas virtuales

Las máquinas virtuales del proyecto tienen diferentes necesidades de recursos dependiendo de las funciones que realizan.

| **Máquina virtual** | **Consumo de recursos** | **Motivo** |
|---|---|---|
| Windows Server | Alto | Utiliza interfaz gráfica y servicios de servidor, como Active Directory. |
| Proxmox VE | Alto | Necesita recursos para gestionar la virtualización y sus servicios. |
| TrueNAS | Alto | Gestiona almacenamiento, discos virtuales y servicios de almacenamiento. |
| OPNsense | Bajo | Realiza funciones de firewall y gestión de red. |
| Debian | Bajo | Funciona principalmente mediante terminal y consume pocos recursos. |
| MikroTik CHR | Bajo | Se utiliza para gestionar el enrutamiento y los servicios de red. |

### 1.3. Recursos que pueden saturarse

Los principales recursos que pueden limitar el rendimiento del equipo son:

- **Memoria RAM:** es uno de los principales límites, ya que el ordenador dispone de 16 GB que deben repartirse entre Windows y todas las máquinas virtuales.
- **Procesador:** puede aumentar su utilización al arrancar varias máquinas simultáneamente, especialmente Windows Server y Proxmox.
- **Almacenamiento:** el disco externo SanDisk de 1 TB contiene los archivos de las máquinas virtuales. TrueNAS necesita espacio para sus discos virtuales y puede generar bastante actividad de lectura y escritura.

El almacenamiento disponible también es importante, ya que las máquinas virtuales pueden ocupar varios GB cada una, especialmente cuando se utilizan discos virtuales de gran capacidad.

## 2. Pruebas de rendimiento

Se analiza el comportamiento del ordenador al ejecutar diferentes combinaciones de máquinas virtuales.

### 2.1. Pruebas individuales

Las máquinas que previsiblemente necesitan más recursos son Windows Server, Proxmox y TrueNAS.

Windows Server destaca por el consumo de memoria RAM debido a su interfaz gráfica y sus servicios. Proxmox necesita recursos para administrar el entorno de virtualización y TrueNAS requiere espacio de almacenamiento para gestionar sus discos.

### 2.2. Pruebas simultáneas

Al disponer de 16 GB de RAM, no resulta recomendable arrancar todas las máquinas virtuales simultáneamente con una asignación elevada de memoria.

Se propone la siguiente organización:

| **Prueba** | **Máquinas arrancadas** | **Valoración** |
|---|---|---|
| 1 | Debian + MikroTik | Consumo bajo |
| 2 | Debian + MikroTik + OPNsense | Consumo bajo |
| 3 | Debian + Windows Server | Consumo medio-alto |
| 4 | Proxmox + TrueNAS | Consumo alto |
| 5 | Proxmox + TrueNAS + Windows Server | Consumo muy alto |

Con esta configuración, se considera que el principal límite del equipo será la memoria RAM, especialmente cuando se ejecuten Windows Server, Proxmox y TrueNAS simultáneamente.

El número máximo de máquinas virtuales dependerá de la memoria asignada a cada una y de los recursos que necesite el sistema anfitrión.

## 3. Optimizaciones aplicadas

A partir del análisis de los recursos disponibles, se proponen dos optimizaciones para mejorar el rendimiento del equipo físico.

### 3.1. Optimización 1 — Ajuste de memoria RAM y procesadores

Se ajustarán los recursos asignados a cada máquina virtual según su función.

| **Máquina virtual** | **RAM recomendada** | **Procesadores virtuales** |
|---|---:|---:|
| Windows Server | 4 GB | 2 |
| Proxmox VE | 4 GB | 2 |
| TrueNAS | 4 GB | 2 |
| OPNsense | 1 GB | 1 |
| Debian | 1 GB | 1 |
| MikroTik CHR | 512 MB | 1 |

Se evitará arrancar simultáneamente todas las máquinas que necesitan más memoria RAM. De esta manera, se reservarán recursos suficientes para el sistema operativo anfitrión.

### 3.2. Optimización 2 — Desactivación de servicios innecesarios

Se reducirán los procesos que se ejecutan automáticamente en las máquinas virtuales.

Las acciones previstas son:

- En Debian, desactivar servicios que no sean necesarios para las funciones del proyecto.
- En Windows Server, evitar ejecutar aplicaciones adicionales y servicios que no se utilicen.
- En TrueNAS, mantener únicamente los servicios necesarios para la gestión del almacenamiento.
- En OPNsense y MikroTik, mantener únicamente los servicios de red necesarios.

También se evitará mantener máquinas virtuales encendidas cuando no se estén utilizando.

## 4. Comprobación de las mejoras

Después de aplicar las optimizaciones, se comparará el comportamiento del equipo antes y después de los cambios.

| **Aspecto** | **Antes de optimizar** | **Después de optimizar** |
|---|---|---|
| Memoria RAM | Mayor consumo por asignaciones excesivas | Recursos ajustados a las necesidades |
| CPU | Posible sobrecarga al arrancar varias máquinas | Menor carga innecesaria |
| Almacenamiento | Espacio ocupado por discos virtuales grandes | Discos dimensionados según las necesidades |
| Máquinas simultáneas | Mayor riesgo de ralentizaciones | Mejor distribución de recursos |

### 4.1. Mejoras esperadas

Con las optimizaciones se pretende:

- Reducir el consumo innecesario de memoria RAM.
- Evitar la saturación del procesador.
- Mejorar el tiempo de arranque de las máquinas virtuales.
- Reducir las ralentizaciones del sistema anfitrión.
- Poder trabajar con varias máquinas virtuales simultáneamente de forma más estable.

## 5. Conclusión final

El análisis del equipo físico permite identificar que la memoria RAM es uno de los recursos más limitados para desarrollar el proyecto ISO-FHW, ya que el ordenador dispone de 16 GB.

Las máquinas virtuales que más recursos necesitan son Windows Server, Proxmox VE y TrueNAS, mientras que Debian, OPNsense y MikroTik CHR tienen unas necesidades más reducidas.

Las optimizaciones propuestas consisten en ajustar la memoria RAM y los procesadores virtuales, además de desactivar servicios innecesarios y apagar las máquinas que no se estén utilizando.

Con estas medidas se consigue una distribución más eficiente de los recursos disponibles y se reduce el riesgo de saturación del ordenador físico.
