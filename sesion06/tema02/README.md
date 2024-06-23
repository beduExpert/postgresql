[`PostgreSQL Avanzado`](../../README.md) > [`Sesión 06`](../README.md)

### 6.3. Restauración de Datos

<img src="../imagenes/img13.jpg" width="45%" align="right" hspace=30>

#### Definición

- Una copia de seguridad física implica copiar los archivos de datos físicos que representan la base de datos en el sistema de archivos. Es una copia del directorio de datos de **PostgreSQL**.

#### Herramientas

- `pg_basebackup`: Una herramienta para realizar copias de seguridad físicas del clúster de **PostgreSQL**.
- Métodos de copia manual, como `rsync` o `tar`, utilizados en combinación con técnicas de archivo de registros transaccionales (WAL) para consistencia.

#### Formato

- Copia directa del directorio de **PostgreSQL**, incluyendo archivo de configuración y registros WAL.

#### Ventajas

- Velocidad: La restauración suele ser más rápida, ya que es una copia directa de los archivos de datos.
- Completa: Incluye todas las bases de datos en el clúster, así como configuraciones y archivos WAL necesarios para la recuperación.

#### Desventajas

- Dependencia del hardware: Los respaldos físicos son específicos del sistema operativo y la arquitectura del hardware en el que se crearon.
- Menos flexibilidad: Generalmente se utilizar para restaurar en la misma versión de **PostgreSQL**.

#### Uso desde línea de comandos

- Actualmente, **PgAdmin 4** no soporta directamente la creación de copias de seguridad físicas a través de su interfaz gŕafica. Sin embargo, puedes utilizar herramientas de línea de comandos como `pg_basebackup` para este propósito.

<br/>

[`Anterior`](../tema01/ejemplo01/README.md) | [`Siguiente`](../tema03/ejemplo02/README.md)
