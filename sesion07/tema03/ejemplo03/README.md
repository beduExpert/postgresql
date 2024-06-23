[`PostgreSQL Avanzado`](../../../README.md) > [`Sesión 07`](../../README.md) > [`Ajuste de Configuración para Rendimiento en PostgreSQL`](../README.md)

### Ejemplo 3

#### 1️⃣ Introducción

En este ejemplo, exploaremos cómo ajustar los parámetros de configuración en PostgreSQL para optimizar el rendimiento del servidor de base de datos. Utilizaremos pgAdmin 4 para acceder y modificar estos parámetros.

---

#### 2️⃣ Objetivos

1. Comprender la importancia de los ajustes de configuración para el rendimiento en PostgreSQL.

2. Identificar y modificar parámetros clave en la configuración de PostgreSQL.

3. Realizar pruebas prácticas para evaluar el impacto de los ajustes en el rendimiento del servidor.

---

#### 3️⃣ Prerrequisitos

- Tener **PostgreSQL** y **pgAdmin 4** instalados.

- Acceso a un servidor con permisos administrativos.

---

#### 4️⃣ Acceso a pgAdmin 4

**Propiedades ACID**

- Abre pgAdmin 4

- Conéctate a tu servidor de PostgreSQL usando las credenciales adecuadas.

--- 

#### 5️⃣ Identificación de Parámetros Clave

**Localización de los Parámetros de Configuración**

1. En pgAdmin 4, selecciona tu servidor PostgreSQL.

2. Navega hasta la sección `Databases`.

3. Haz clic con el botón derecho en la base de datos que deseas realizar los ajustes y selecciona `Query Tool`.

**Ejemplo de Parámetros Importantes**

- **shared_buffers**: Controla la cantidad de memoria asignada para almacenar datos recuperados y el índice de los bloques de disco recientemente leídos.

   ```sql
   SHOW shared_buffers;
   ```

- **work_mem**: Especifica la cantidad de memoria utilizada por las operaciones de clasificación interna y de creación de índices.

   ```sql
   SHOW work_mem;
   ```

- **maintenance_work_mem**: Define la cantidad de memoria que el servidor puede utilizar para tareas de mantenimiento, como la indexación y el VACUUM.

   ```sql
   SHOW maintenance_work_mem;
   ```

---

#### 6️⃣ Modificación de Parámetros de Configuración

**Ejemplo de Modificación**

1. Cambia el valor de `shared_buffers` a 2GB:

   ```sql
   ALTER SYSTEM SET shared_buffers TO '2GB';
   ```

2. Aplica los cambios:

   ```sql
   SELECT pg_reload_conf();
   ```

**Modificación de otros Parámetros**

- Ajusta `work_mem` y `maintenance_work_mem` según las necesidades y el tamaño de tu base de datos.

---

#### 7️⃣ Evaluación de Rendimiento

1. Ejecuta consultas de prueba antes y después de realizar los ajustes de configuración.

2. Utiliza la herramienta `EXPLAIN` para comparar los planes de ejecución y la mejora del rendimiento.

   ```sql
   EXPLAIN SELECT * FROM tabla WHERE columna = 'valor';
   ```

---

#### 8️⃣ Monitorización y Ajustes Adicionales

1. Utiliza herramientas como `pg_stat_statements` y `pg_stat_activity` para monitorear el impacto de los cambios en el rendimiento.

2. Ajusta los parámetros según el perfil de carga y los patrones de acceso a datos observados.

--- 

#### 9️⃣ Conclusión

A través de este ejemplo, has aprendido cómo ajustar los parámetros de configuración en PostgreSQL para mejorar el rendimiento del servidor de base de datos. Es importante realizar pruebas y monitorear continuamente el sistema para optimizar los ajustes según las necesidades específicas de tu aplicación y entorno de base de datos. Esto garantiza que PostgreSQL funcione de manera eficiente y optimizada para manejar cargas de trabajo variadas y exigentes.


[`Anterior`](../README.md) | [`Siguiente`](../../tema04/README.md)
