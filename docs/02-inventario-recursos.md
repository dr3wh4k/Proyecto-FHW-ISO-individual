# TASCA 2 — Equips i perifèrics

## 1. Introducción

El objetivo de esta tarea es realizar un inventario del hardware de los equipos utilizados habitualmente, tanto en casa como en clase. Se analizarán sus características principales, los recursos disponibles y su capacidad para trabajar con diferentes sistemas operativos y máquinas virtuales.

También se realizará una comparación entre ambos equipos para identificar posibles cuellos de botella y proponer mejoras que permitan optimizar su rendimiento.

## 2. Inventario de los equipos

### 2.1. Ordenador de casa

El ordenador de casa se utiliza para realizar las tareas del proyecto individual, trabajar con diferentes herramientas informáticas y ejecutar aplicaciones relacionadas con la virtualización y la administración de sistemas.

| Componente | Características |
|---|---|
| Tipo de equipo | Ordenador de sobremesa |
| Procesador | Intel Core i7 (modelo exacto pendiente de identificar) |
| Memoria RAM | 16 GB |
| Almacenamiento interno | 1TB |
| Almacenamiento externo | Disco SanDisk de 1 TB |
| Tarjeta gráfica | No tiene |
| Sistema operativo | Windows 11 |

**Almacenamiento externo**

Para el desarrollo del proyecto individual se utiliza un disco SanDisk de 1 TB, destinado a almacenar archivos, máquinas virtuales, imágenes ISO, copias de seguridad y documentación.

- Fabricante: SanDisk.
- Capacidad: 1 TB.
- Modelo exacto: pendiente de identificar.
- Tipo de conexión: pendiente de comprobar (USB u otra).
- Tecnología: pendiente de identificar (SSD o HDD).

### 2.2. Ordenador portátil de clase

El ordenador portátil de clase se utiliza para realizar las actividades y prácticas del ciclo formativo, así como para trabajar con las herramientas de administración de sistemas y redes.

| Componente | Características |
|---|---|
| Tipo de equipo | Ordenador portátil |
| Procesador | Intel Core i5 |
| Memoria RAM | 32 GB |
| Almacenamiento interno | 1 TB |
| Almacenamiento externo | Disco SanDisk de 1 TB |
| Tarjeta gráfica | NO TIENE |
| Sistema operativo | Lliurex |

## 3. Comparativa de los equipos

A continuación, se comparan los recursos conocidos de ambos equipos.

| Característica | Ordenador de casa | Portátil de clase |
|---|---|---|
| Tipo | Sobremesa | Portátil |
| Procesador | Intel Core i7 | Pendiente |
| Memoria RAM | 16 GB | 32 GB |
| Almacenamiento externo | SanDisk 1 TB | SanDisk 1 TB |
| Uso principal | Proyecto individual y prácticas | Actividades y prácticas de clase |

### 3.1. Análisis de rendimiento

**Ordenador de casa**

El ordenador dispone de un procesador Intel Core i7 y 16 GB de memoria RAM. Estas características permiten trabajar con aplicaciones habituales de administración de sistemas, programación y redes.

Sin embargo, los 16 GB de RAM pueden convertirse en una limitación al ejecutar varias máquinas virtuales simultáneamente, especialmente si se utilizan sistemas operativos que requieren una cantidad considerable de memoria.

El disco SanDisk de 1 TB proporciona capacidad adicional para almacenar los recursos del proyecto. Su rendimiento dependerá del modelo y de la interfaz de conexión.

**Portátil de clase**

El portátil dispone de 32 GB de memoria RAM, el doble que el ordenador de casa. Esta cantidad de memoria ofrece mayor margen para ejecutar varias máquinas virtuales y trabajar con diferentes servicios simultáneamente.

No obstante, para realizar una comparación completa será necesario conocer también el modelo del procesador, el almacenamiento y las características de red.

## 4. Identificación de posibles cuellos de botella

Un cuello de botella se produce cuando uno de los componentes limita el rendimiento general del equipo, impidiendo aprovechar correctamente el resto de los recursos.

### 4.1. Ordenador de casa

| Recurso | Posible limitación | Solución propuesta |
|---|---|---|
| CPU | Pendiente de comprobar según el modelo y la carga de trabajo | Evitar ejecutar tareas innecesarias simultáneamente |
| RAM | Los 16 GB pueden limitar la ejecución de varias máquinas virtuales | Asignar la memoria de forma equilibrada y cerrar aplicaciones innecesarias |
| Disco | El rendimiento depende del modelo del disco y su conexión | Utilizar el disco más rápido para las máquinas virtuales |
| Red | Pendiente de comprobar | Revisar la conexión y los adaptadores de red |

### 4.2. Portátil de clase

| Recurso | Posible limitación | Solución propuesta |
|---|---|---|
| CPU | Pendiente de identificar | Ajustar los recursos de las máquinas virtuales |
| RAM | Dispone de 32 GB, aunque puede agotarse con muchas máquinas virtuales | Controlar el consumo de memoria |
| Disco | Capacidad y velocidad pendientes de identificar | Revisar el espacio disponible y el rendimiento |
| Red | Pendiente de comprobar | Verificar la conectividad y los adaptadores |

## 5. Pruebas de diagnóstico del hardware

Para comprobar el estado de los equipos se realizarán pruebas de diagnóstico sobre memoria, almacenamiento y red.

Los resultados se incorporarán una vez ejecutadas las herramientas correspondientes.

### 5.1. Diagnóstico de memoria RAM

**Objetivo:** comprobar el estado de la memoria y observar su consumo durante la ejecución de aplicaciones y máquinas virtuales.

| Equipo | Herramienta | Resultado |
|---|---|---|
| Casa | Diagnóstico de memoria del sistema / MemTest86 | Pendiente |
| Clase | Diagnóstico de memoria del sistema / MemTest86 | Pendiente |

Se registrarán los posibles errores detectados y el consumo de memoria durante las pruebas.

### 5.2. Diagnóstico de almacenamiento

**Objetivo:** comprobar el estado de los discos y analizar su rendimiento.

| Equipo | Herramienta | Resultado |
|---|---|---|
| Casa | CrystalDiskInfo / herramienta SMART | Pendiente |
| Casa | CrystalDiskMark | Pendiente |
| Disco SanDisk 1 TB | CrystalDiskInfo y CrystalDiskMark, si son compatibles | Pendiente |
| Clase | CrystalDiskInfo / herramienta SMART | Pendiente |

Se comprobarán los siguientes aspectos:

- Estado de salud del disco.
- Temperatura.
- Espacio disponible.
- Velocidad de lectura.
- Velocidad de escritura.

### 5.3. Diagnóstico de red

**Objetivo:** comprobar la conectividad y el funcionamiento de las interfaces de red.

| Equipo | Herramienta | Resultado |
|---|---|---|
| Casa | `ipconfig /all` | Pendiente |
| Clase | `ipconfig /all` | Pendiente |
| Casa | `ping` | Pendiente |
| Clase | `ping` | Pendiente |

Se analizarán:

- Dirección IP.
- Máscara de subred.
- Puerta de enlace.
- Servidores DNS.
- Conectividad con otros equipos.
- Posibles pérdidas de paquetes.

## 6. Registro de resultados

Una vez realizadas las pruebas, se completará la siguiente tabla para documentar las condiciones y los resultados obtenidos.

| Equipo | Prueba | Herramienta | Condiciones | Resultado e interpretación |
|---|---|---|---|---|
| Casa | Memoria | | | |
| Casa | Disco | | | |
| Casa | Red | | | |
| Clase | Memoria | | | |
| Clase | Disco | | | |
| Clase | Red | | | |

## 7. Conclusiones

Los dos equipos presentan características diferentes en cuanto a sus recursos disponibles.

El ordenador de casa dispone de un procesador Intel Core i7 y 16 GB de RAM, además de un disco SanDisk de 1 TB utilizado para el proyecto individual. Su principal limitación potencial es la memoria RAM cuando se ejecutan varias máquinas virtuales simultáneamente.

Por otro lado, el portátil de clase dispone de 32 GB de RAM, lo que proporciona mayor capacidad para trabajar con varias máquinas virtuales y servicios al mismo tiempo.

Para determinar cuál de los dos equipos ofrece un mejor rendimiento general será necesario completar el inventario del procesador, almacenamiento y red, además de ejecutar las pruebas de diagnóstico.

## 8. Evidencias

Se incorporarán capturas de pantalla y registros de las pruebas realizadas.

- [ ] Información del procesador del ordenador de casa.
- [ ] Información de la memoria RAM del ordenador de casa.
- [ ] Información del disco SanDisk de 1 TB.
- [ ] Información del procesador del portátil de clase.
- [ ] Información de la memoria RAM del portátil.
- [ ] Diagnóstico de memoria de ambos equipos.
- [ ] Diagnóstico de almacenamiento de ambos equipos.
- [ ] Pruebas de conectividad de red.
- [ ] Comparativa del consumo de recursos.

