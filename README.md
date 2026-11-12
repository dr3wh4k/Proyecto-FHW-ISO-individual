# ISO-FHW — Infraestructura de Sistemas y Servicios de Red

Repositorio dedicado a la documentación técnica, planificación, implementación y configuración de una infraestructura de red empresarial virtualizada, desarrollada como parte del proyecto de **ISO-FHW del Ciclo Formativo de Grado Superior ASIX**.

---

## Descripción del Proyecto

Este repositorio contiene la documentación técnica y las evidencias de configuración de un entorno de infraestructura empresarial virtualizado mediante **VirtualBox**, con el objetivo de simular una red corporativa y desplegar diferentes servicios de sistemas, comunicaciones, seguridad y almacenamiento.

El proyecto contempla la instalación, configuración e interconexión de diferentes plataformas y sistemas operativos, buscando reproducir una infraestructura empresarial funcional, segmentada y administrable.

Entre las tecnologías principales utilizadas se encuentran:

- **Proxmox VE:** plataforma de virtualización y gestión de máquinas virtuales.
- **MikroTik CHR:** router para la gestión del direccionamiento y enrutamiento de red.
- **OPNsense:** firewall para el control y filtrado del tráfico de red.
- **TrueNAS:** plataforma de almacenamiento y gestión de recursos compartidos.
- **Debian:** servidor Linux para servicios de red y configuración de cortafuegos mediante `nftables`.
- **Windows Server 2025:** plataforma para la implementación de servicios empresariales, como Active Directory y DNS.

---

## Índice de Documentación

A continuación se enlazan los informes técnicos correspondientes a las diferentes tareas del proyecto, organizados en la carpeta `docs/`:

- **[Tasca 0 - Predicciones Iniciales](docs/00-predicciones.md):** Análisis inicial del proyecto, planificación de la infraestructura y previsión de los recursos necesarios para su implementación.

- **Tasca 1 - Diseño de la Infraestructura:** Planificación de los sistemas, servicios y componentes que forman parte del entorno empresarial.

- **Tasca 2 - Inventario y Recursos:** Identificación de los recursos hardware y software necesarios para desplegar la infraestructura.

- **Tasca 3 - Diseño de Red:** Definición del direccionamiento IP, topología, interconexiones y configuración de los dispositivos de red.

- **Tasca 4 - Comunicaciones y Seguridad:** Configuración de los elementos de comunicaciones, enrutamiento, firewall y filtrado del tráfico.

- **[Tasca 5 - Instalación de la Plataforma](docs/05-instalacion.md):** Documentación del despliegue de Proxmox VE y de los diferentes sistemas que componen la infraestructura virtualizada.

- **Tasca 6 - Configuración de Servicios:** Implementación y configuración de los servicios de red y sistemas empresariales.

- **Tasca 7 - Almacenamiento:** Configuración de TrueNAS y planificación de los recursos de almacenamiento compartido.

- **Tasca 8 - Seguridad y Administración:** Configuración de mecanismos de protección, control de acceso y administración de los sistemas.

- **Tasca 9 - Pruebas y Verificación:** Comprobación de conectividad, funcionamiento de los servicios, comunicaciones y estabilidad de la infraestructura.

- **[Tasca 10 - Conclusiones](docs/10-conclusiones.md):** Evaluación final del proyecto, incidencias encontradas, soluciones aplicadas y posibles mejoras.

---

## Topología de Red

La infraestructura utiliza como base la red interna `192.168.25.0/24`, con el siguiente direccionamiento previsto para los principales componentes:

| Dispositivo | Dirección IP |
|---|---|
| MikroTik CHR | `192.168.25.1` |
| OPNsense | `192.168.25.2` |
| TrueNAS | `192.168.25.10` |
| Proxmox VE | `192.168.25.20` |
| Windows Server | `192.168.25.30` |
| Debian | `192.168.25.40` |

---

## Organización del Repositorio

La estructura del repositorio está organizada para separar la documentación, los esquemas técnicos y las evidencias del proyecto.

```text
iso-fhw-empresa/
│
├── README.md
│
├── docs/
│   ├── 00-predicciones.md
│   ├── 01-...
│   ├── 02-...
│   ├── 03-...
│   ├── 04-...
│   ├── 05-instalacion.md
│   ├── 06-...
│   ├── 07-...
│   ├── 08-...
│   ├── 09-...
│   └── 10-conclusiones.md
│
├── diagramas/
│   └── topologia.md
│
└── evidencias/
    └── README.md
```

- `docs/`: informes técnicos en Markdown correspondientes a las diferentes tareas del proyecto.
- `diagramas/`: esquemas de topología, interconexión y arquitectura de la infraestructura.
- `evidencias/`: capturas de pantalla, configuraciones, registros y pruebas de funcionamiento.

---

## Objetivos del Proyecto

- Desplegar una infraestructura empresarial virtualizada.
- Implementar y administrar diferentes sistemas operativos y servidores.
- Diseñar una arquitectura de red con direccionamiento IP estructurado.
- Configurar servicios de enrutamiento, firewall y comunicaciones.
- Implementar soluciones de almacenamiento centralizado.
- Aplicar medidas de seguridad y control del tráfico de red.
- Documentar técnicamente los procedimientos, configuraciones e incidencias.
- Verificar el funcionamiento de los diferentes componentes mediante pruebas.

---

*Proyecto académico desarrollado en el marco del Ciclo Formativo de Grado Superior de Administración de Sistemas Informáticos en Red (ASIX).* 
