[`PostgreSQL Avanzado`](../README.md)

# Sesión 09: Monitoreo y Mantenimiento Proactivo

## 🌿 Introducción

El monitoreo y mantenimiento proactivo de PostgreSQL es crucial para garantizar la disponibilidad, el rendimiento y la integridad de los datos en una base de datos de producción. Este curso avanzado cubrirá las herramientas y técnicas necesarias para monitorear eficazmente PostgreSQL, realizar el mantenimiento de la base de datos y automatizar tareas preventivas.

## 🎯 Objetivos Generales

1. Comprender las herramientas y técnicas para monitorear PostgreSQL eficazmente.
2. Realizar tareas de mantenimiento proactivo en la base de datos para optimizar el rendimiento.
3. Automatizar tareas de mantenimiento y monitoreo para asegurar una administración eficiente.

## 📚 Temario

1. **Monitoreo de PostgreSQL**
    - Objetivo: Utilizar herramientas de monitoreo para supervisar el rendimiento y la salud de PostgreSQL.
    - Subtemas:
      - Herramientas de monitoreo (pg_stat, pgBadger, etc.)
      - Métricas y alertas importantes

2. **Mantenimiento de la Base de Datos**
    - Objetivo: Realizar tareas de mantenimiento para asegurar el buen funcionamiento de PostgreSQL.
    - Subtemas:
      - Vacío y autovacío (vacuum)
      - Reindexado y análisis (reindex, analyze)

3. **Tareas Automatizadas**
    - Objetivo: Automatizar tareas de mantenimiento y monitoreo utilizando cron y pg_cron.
    - Subtemas:
      - Programación de tareas con cron y pg_cron
      - Mantenimiento preventivo

## 🚀 Desarrollo

---

<details><summary><h3>Monitoreo de PostgreSQL</h3></summary>
<br/>

#### Herramientas de Monitoreo (pg_stat, pgBadger, etc.)

Existen diversas herramientas para monitorear PostgreSQL, cada una con capacidades específicas para ofrecer visibilidad y alertas sobre el estado de la base de datos.

- **pg_stat**: Conjunto de vistas y funciones internas que proporcionan información sobre la actividad y el estado del servidor.
  - Ejemplo de uso:
    ```sql
    SELECT * FROM pg_stat_activity;
    SELECT * FROM pg_stat_database;
    ```

- **pgBadger**: Herramienta que analiza los archivos de registro de PostgreSQL y genera reportes detallados.
  - Instalación y uso básico:
    ```bash
    pg_badger /var/log/postgresql/postgresql.log -o report.html
    ```

#### Métricas y Alertas Importantes

Es fundamental conocer las métricas clave y configurar alertas para detectar problemas antes de que afecten el rendimiento de la base de datos.

- **Métricas Clave**:
  - Uso de CPU y memoria.
  - Tiempos de respuesta de consultas.
  - Tasa de transacciones por segundo.
  - Uso del almacenamiento y crecimiento de la base de datos.

- **Configuración de Alertas**:
  - Utilizar herramientas como Nagios, Zabbix o Prometheus para configurar alertas basadas en las métricas clave.

<br/>
</details>

---

<details><summary><h3>Mantenimiento de la Base de Datos</h3></summary>
<br/>

#### Vacío y Autovacío (VACUUM)

El comando `VACUUM` es esencial para recuperar espacio en disco ocupado por datos eliminados y mantener el rendimiento de las consultas.

- **VACUUM**: Libera espacio en disco y actualiza estadísticas internas.
  - Uso básico:
    ```sql
    VACUUM;
    VACUUM FULL;
    ```

- **Autovacío**: Automatiza el proceso de `VACUUM`.
  - Configuración en `postgresql.conf`:
    ```ini
    autovacuum = on
    autovacuum_max_workers = 3
    autovacuum_naptime = 1min
    ```

#### Reindexado y Análisis (REINDEX, ANALYZE)

El reindexado y el análisis son cruciales para mantener los índices eficientes y las estadísticas de las tablas actualizadas.

- **REINDEX**: Reorganiza los índices de una tabla o base de datos.
  - Uso básico:
    ```sql
    REINDEX TABLE my_table;
    REINDEX DATABASE my_database;
    ```

- **ANALYZE**: Actualiza las estadísticas utilizadas por el planificador de consultas.
  - Uso básico:
    ```sql
    ANALYZE;
    ANALYZE my_table;
    ```

<br/>
</details>

---

<details><summary><h3>Tareas Automatizadas</h3></summary>
<br/>

#### Programación de Tareas con cron y pg_cron

Automatizar tareas de mantenimiento y monitoreo es esencial para asegurar una administración eficiente y proactiva de la base de datos.

- **cron**: Herramienta de programación de tareas en Unix/Linux.
  - Ejemplo de configuración:
    ```bash
    0 2 * * * /usr/bin/vacuumdb -U postgres -d my_database -z
    ```

- **pg_cron**: Extensión de PostgreSQL para programación de tareas.
  - Instalación y configuración:
    ```sql
    CREATE EXTENSION pg_cron;
    ```

  - Ejemplo de uso:
    ```sql
    SELECT cron.schedule('0 2 * * *', 'VACUUM FULL my_table');
    ```

#### Mantenimiento Preventivo

El mantenimiento preventivo implica realizar tareas regulares para prevenir problemas antes de que ocurran.

- **Tareas Preventivas**:
  - Realizar `VACUUM` y `ANALYZE` regularmente.
  - Reindexar tablas periódicamente.
  - Monitorear el crecimiento de las tablas y ajustar la configuración de autovacío según sea necesario.



<br/>
</details>

---

### 💯 Conclusión

El monitoreo y mantenimiento proactivo de PostgreSQL es fundamental para asegurar la disponibilidad, el rendimiento y la integridad de los datos. Esta sesión	 ha cubierto las herramientas y técnicas necesarias para monitorear eficazmente PostgreSQL, realizar tareas de mantenimiento y automatizar tareas preventivas. Con este conocimiento, los administradores de bases de datos pueden asegurar que sus sistemas sean robustos, eficientes y capaces de manejar las demandas de las aplicaciones modernas.

### 🤓 Proyecto Modular

---

<details><summary><h3>Preparando el monitoreo</h3></summary>
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
- [ ] Preparando el monitoreo
- [ ] Migración de datos
- [ ] Presentación del proyecto

---
 
#### :dart: Avance del Proyecto 8/10: Optimizando consultas

##### Actividad

⏰ Tiempo estimado: *60 minutos*

- Investiga y describe las herramientas disponibles para el monitoreo de PostgreSQL (por ejemplo, pg_stat, pgBadger).

- Elabora un reporte detallando las métricas y alertas importantes que deben monitorearse.

- Propón un plan de monitoreo adecuado para tu proyecto.

**Ejemplo**:

- Redacta un documento en la carpeta docs que explique las herramientas de monitoreo y proponga un plan de monitoreo.

</details>

---

[`< Regresar`](../README.md)
