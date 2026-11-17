# Tasca 6 – Configuración y comparación de RAID

## 1. Objetivo

El objetivo de esta práctica es implementar y comparar tres configuraciones RAID diferentes utilizando discos virtuales en una máquina virtual TrueNAS SCALE.

Se pretende comprobar su funcionamiento, analizar su tolerancia a fallos y estudiar las ventajas e inconvenientes de cada configuración.

## 2. Entorno de pruebas

| Parámetro | Características |
|---|---|
| Sistema operativo | TrueNAS SCALE |
| Virtualizador | Oracle VirtualBox |
| Almacenamiento | Discos virtuales |
| Capacidad de cada disco | 50 GB |
| RAID implementados | Stripe, Mirror y RAIDZ1 |

## 3. Tipos de RAID implementados

### 3.1 RAID 0 – Stripe

Se configura un pool llamado `RAID0_TEST` utilizando dos discos virtuales de 50 GB mediante Stripe.

**Características:**
- Distribuye los datos entre los dos discos.
- Ofrece mayor rendimiento de lectura y escritura.
- Capacidad aproximada: 100 GB.
- No dispone de redundancia.
- Si falla un disco, se pierde la disponibilidad del pool.

### 3.2 RAID 1 – Mirror

Se configura un pool llamado `BACKUPS` utilizando dos discos virtuales de 50 GB mediante Mirror.

**Características:**
- Duplica la información en ambos discos.
- Permite soportar el fallo de uno de ellos.
- Capacidad aproximada: 50 GB.
- Proporciona redundancia y mayor disponibilidad de los datos.

### 3.3 RAID 5 – RAIDZ1

Se configura un pool llamado `RAIDZ1_TEST` utilizando tres discos virtuales de 50 GB mediante RAIDZ1 en TrueNAS.

**Características:**
- Distribuye los datos y la paridad entre los discos.
- Permite soportar el fallo de un disco.
- Capacidad aproximada: 100 GB.
- Ofrece un equilibrio entre capacidad y protección de datos.

## 4. Verificación del funcionamiento

Para comprobar los diferentes tipos de RAID se realizan pruebas de escritura y lectura de archivos, así como simulaciones de fallo de discos.

| RAID | Prueba realizada | Resultado |
|---|---|---|
| RAID 0 | Simulación de fallo de un disco | No se pierden datos porque el mirror pasa al otro disco |
| RAID 1 | Simulación de fallo de un disco | Los datos siguen disponibles gracias al otro disco. |
| RAIDZ1 | Simulación de fallo de un disco | 	Los datos siguen disponibles gracias a la paridad. |

Se comprueba el estado de los pools desde la interfaz de TrueNAS y mediante el comando:

```bash
zpool status
```

## 5. Comparación y conclusiones

| Tipo RAID | Rendimiento | Redundancia | Capacidad |
|---|---|---|---|
| RAID 0 | Alto | No | 100 GB |
| RAID 1 | Bueno | Sí | 50 GB |
| RAIDZ1 | Bueno | Sí | 100 GB |

**Conclusión:**

La implementación de los tres tipos de RAID permite comprobar las diferencias entre rendimiento, capacidad y protección de datos.

RAID 0 destaca por su rendimiento y aprovechamiento del almacenamiento, pero no protege frente a fallos.

RAID 1 proporciona una mayor seguridad mediante la duplicación de datos, mientras que RAIDZ1 permite aprovechar mejor la capacidad de varios discos manteniendo tolerancia al fallo de uno.

Para el almacenamiento de copias de seguridad de la infraestructura empresarial se considera especialmente interesante utilizar Mirror o RAIDZ1, ya que ofrecen protección frente al fallo de un disco.
