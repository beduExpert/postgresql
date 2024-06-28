[`PostgreSQL Avanzado`](../README.md)

# Sesión 10: Actualizaciones y Migraciones en PostgreSQL

## 🌿 Introducción

En el entorno dinámico y en constante evolución de las bases de datos, mantener PostgreSQL actualizado y gestionar migraciones efectivas es crucial para asegurar el rendimiento, la seguridad y la integridad de los datos. Esta sesión está diseñada para proporcionar una comprensión integral de los procesos de actualización y migración en PostgreSQL, abordando tanto los aspectos teóricos como prácticos.

## 🎯 Objetivos Generales

1. Comprender la importancia de mantener PostgreSQL actualizado.
2. Desarrollar habilidades prácticas para planificar y ejecutar actualizaciones y migraciones.
3. Aprender a realizar pruebas y validaciones post-migración para asegurar la integridad y el rendimiento de los datos.

## 📚 Temario

1. **Actualizaciones del Sistema:**
   - Planificación y ejecución de actualizaciones menores.
   - Actualizaciones mayores y sus desafíos.

2. **Migraciones de Bases de Datos:**
   - Migración desde otros SGBD a PostgreSQL.
   - Herramientas y técnicas de migración.

3. **Pruebas y Validación:**
   - Estrategias de pruebas post-migración.
   - Validación de datos y desempeño.

## 🚀 Desarrollo

---

<details><summary><h3>Actualizaciones del Sistema</h3></summary>
<br/>

#### Planificación y ejecución de actualizaciones menores
Las actualizaciones menores en PostgreSQL se enfocan en correcciones de errores y mejoras de seguridad sin modificar la estructura de datos ni la API. Estas actualizaciones son cruciales para mantener el sistema seguro y estable.

- **Pasos para la actualización menor:**
  1. Realizar una copia de seguridad completa.
  2. Leer las notas de la versión.
  3. Probar en un entorno de desarrollo.
  4. Planificar el tiempo de inactividad.
  5. Ejecutar la actualización.

- **Ejemplo:**
  ```sh
  sudo apt-get update
  sudo apt-get install postgresql-13
  psql -c "SELECT version();"
  ```

#### Actualizaciones mayores y sus desafíos
Las actualizaciones mayores incluyen cambios significativos en la estructura de datos, funcionalidades y API. Requieren una planificación más detallada y pueden implicar tiempo de inactividad significativo.

- **Pasos para la actualización mayor:**
  1. Evaluación y planificación.
  2. Pruebas extensivas.
  3. Documentación y comunicación.
  4. Ejecución de la actualización.

- **Ejemplo:**
  ```sh
  sudo apt-get install postgresql-14
  pg_dumpall -U postgres > backup.sql
  pg_ctlcluster 13 main stop
  pg_ctlcluster 14 main start
  psql -U postgres -f backup.sql
  ```

<br/>
</details>

---

<details><summary><h3>Migraciones de Bases de Datos</h3></summary>
<br/>

####Migración desde otros SGBD a PostgreSQL
La migración de bases de datos desde otros sistemas de gestión de bases de datos (SGBD) a PostgreSQL puede ser un proceso complejo que requiere planificación y ejecución cuidadosa.

- **Pasos para la migración:**
  1. Evaluar la compatibilidad.
  2. Seleccionar herramientas de migración.
  3. Planificación y ejecución.

- **Ejemplo:**
  ```sh
  pgloader mysql://root:password@localhost/source_db postgresql://postgres:password@localhost/target_db
  ```

#### Herramientas y técnicas de migración
Existen diversas herramientas y técnicas para facilitar la migración de bases de datos a PostgreSQL.

- **Herramientas comunes:**
  1. pg_dump/pg_restore.
  2. Foreign Data Wrapper (FDW).
  3. pgAdmin y otros GUI.

- **Ejemplo:**
  ```sh
  pg_dump -U postgres source_db > source_db.sql
  createdb -U postgres target_db
  psql -U postgres target_db < source_db.sql
  ```

<br/>
</details>

---

<details><summary><h3>Pruebas y Validación</h3></summary>
<br/>

##### Estrategias de pruebas post-migración
Las pruebas post-migración son esenciales para asegurar que los datos se han migrado correctamente y que el rendimiento de la base de datos es óptimo.

- **Pasos para las pruebas:**
  1. Validación de datos.
  2. Pruebas de rendimiento.
  3. Pruebas funcionales.

- **Ejemplo:**
  ```sh
  pg_dump -U postgres --column-inserts --data-only source_db > source_data.sql
  pg_restore -U postgres --data-only -d target_db source_data.sql
  md5sum source_data.sql
  md5sum target_data.sql
  ```

#### Validación de datos y desempeño
La validación asegura que los datos y el rendimiento cumplen con los requisitos esperados después de la migración.

- **Técnicas de validación:**
  1. Checksums y herramientas de comparación.
  2. Monitoreo continuo.

- **Ejemplo:**
  ```sh
  pgbench -i -s 10 target_db
  pgbench -c 10 -j 2 -T 60 target_db
  ```

<br/>
</details>

---

### 💯 Conclusión

Mantener PostgreSQL actualizado y gestionar migraciones efectivas son tareas esenciales para cualquier administrador de bases de datos. A través de este módulo, los adquirirás las habilidades necesarias para planificar, ejecutar y validar actualizaciones y migraciones, asegurando así la continuidad y eficiencia de sus sistemas de bases de datos.

<details><summary><h3>Migración de datos / Presentación del proyecto</h3></summary>
<br/>

Con el fin de que puedas poner todo tu conocimiento en práctica a lo largo de este módulo se realizarán distintas actividades que te permitirán ir construyendo un proyecto de manera progresiva y de manera guiada por los expertos. Este proyecto será el entregable final de todo del módulo y se dividirá en las siguientes etapas:

- [x] Creación de un repositorio   
- [x] Obtención de datos   
- [x] Configuración del entorno SQL   
- [x] Diseño de la base de datos
- [x] Gestión de usuarios
- [x] Creando una copia de seguridad
- [x] Optimizando consultas
- [x] Preparando un proceso de réplica y alta disponibilidad
- [x] Preparando el monitoreo
- [ ] Migración de datos
- [ ] Presentación del proyecto

---
 
#### :dart: Avance del Proyecto 9/10: Migración de datos

##### Actividad

⏰ Tiempo estimado: *60 minutos*

- Investiga y describe las técnicas y herramientas disponibles para la migración de datos hacia PostgreSQL desde otros sistemas de gestión de bases de datos.
- Elabora un reporte detallando los pasos y consideraciones importantes para realizar una migración exitosa.
- Propón un plan de migración para tu proyecto.


**Ejemplo**:

- Redacta un documento en la carpeta docs que explique las técnicas de migración y proponga un plan de migración.

---

#### :dart: Avance del Proyecto 10/10: Presentación del proyecto

##### Actividad

⏰ Tiempo estimado: *60 minutos*

- Prepara una presentación de 5 minutos que resuma el proyecto completo.
- Incluye los objetivos, metodología, resultados y conclusiones.
- Asegúrate de que la presentación sea clara y concisa, y que destaque los aspectos más importantes del proyecto.
- Entrega el enlace al repositorio de GitHub con todos los puntos de la lista de cotejo completados.


**Ejemplo**:

- Usa herramientas como PowerPoint o Google Slides para crear la presentación.
- Guarda el archivo de la presentación en formato PDF en la carpeta docs.
- Comparte el enlace del repositorio y la presentación con el experto.

</details>

---

[`< Regresar`](../README.md)
