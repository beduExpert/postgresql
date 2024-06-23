[`PostgreSQL Avanzado`](../../README.md) > [`Sesión 06`](../README.md)

### 6.4. Estrategias de Recuperación

<img src="../imagenes/img13.jpg" width="45%" align="right" hspace=30>

#### Punto en el Tiempo (PITR)
*Point-In-Time-Recovery*

- Permite recuperar la base de datos a un momento específico en el tiempo.

- Requiere copias de seguridad base y archivos de registro (WAL).

#### Pasos básicos

1. Realizar una copia de seguridad base.

2. Configurar la retención de WAL.

3. Restaurar desde la copia de seguridad base y aplicar los archivos WAL hasya el punto deseado.

#### Configuración WAL

```conf
wal_level = replica
archive_mode = on
archive_command = 'cp %p /ruta/a/archive/%f'
```

#### Archivos de Registro (WAL)

- Registro de todas las transacciones realizadas en la base de datos.

- Utilizados para replicación y recuperación de fallos.

#### 🧐 Actividades

- [`Ejemplo 3`](ejemplo03/README.md)

<br/>

[`Anterior`](../tema01/ejemplo01/README.md) | [`Siguiente`](ejemplo03/README.md)
