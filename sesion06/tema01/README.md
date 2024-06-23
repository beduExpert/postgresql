[`PostgreSQL Avanzado`](../../README.md) > [`Sesión 06`](../README.md)

### 6.1. Copia de Seguridad Lógica

<img src="../imagenes/img13.jpg" width="45%" align="right" hspace=30>

#### Definición

- Una copia de seguridad lógica se refiere a la exportación de los datos y la estructura de la base de datos en formato plano **SQL** o en un formato binario especial que puede ser restaurado mediante herramientas específicas.

#### Herramientas

- `pg_dump`: Se utiliza para realizar copias de seguridad de bases de datos individuales.
- `pg_dumpall`: Se utiliza para hacer copias de seguridad de todas las bases de datos en un clúster de **PostgreSQL**, incluyendo los datos globales como roles y permisos.

#### Formato

- Puede generar archivos en formato **SQL** (archivo plano) o en un formato binario (tar, custom).

#### Ventajas

- Idependencia del hardware: Los archivos de respaldo son independientes del sistema operativo y de la arquitectura del hardware.
- Flexibilidad: Permite restaurar en diferentes versiones de **PostgreSQL**.
- Granularidad: Puedes elegir qué tablas o esquemas respaldar.

#### Desventajas

- Tiempo de restauración: Puede ser más lento en comparación con la restauración física, especialmente para bases de datos grandes.
- Tamaño de respaldo: Puede ser más grande en comparación con los respaldos físicos.

#### 🧐 Actividades

- [`Ejemplo 1`](ejemplo01/README.md)

<br/>

[`Anterior`](../circulo_estudio/reto05/README.md) | [`Siguiente`](ejemplo01/README.md)
