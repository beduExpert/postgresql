[`PostgreSQL Avanzado`](../README.md)

## Sesión 04: Diseño de Bases de Datos en PostgreSQL

### 🌿 Presentación 

En esta sesión se profundiza en el diseño y modelado de bases de datos en PostgreSQL. Se cubrirá la creación de esquemas, tablas, relaciones y llaves, así como la implementación de índices y vistas para optimizar el rendimiento y la eficiencia de las consultas.

### 🎯 Objetivo

Aprender a diseñar bases de datos eficientemente en PostgreSQL, comprendiendo el modelado de datos, la creación de esquemas y la gestión de índices y vistas.

### 👨‍💻 Hands-on para iniciar

<details>
<summary style= "background: ghostwhite; padding: 10px; border: 1px solid lightgray; margin: 0px;"><strong>Modelado de datos</strong><br/></summary>
<br/>

#### Objetivo
Crear esquemas y tablas, y comprender los tipos de datos disponibles en PostgreSQL.

#### Materiales Necesarios:
- PostgreSQL 16 y pgAdmin 4 instalados en tu sistema.
- Conexión a Internet (opcional para consutlar documentación).

#### Tiempo Estimado: 


#### Instrucciones paso a paso

**Paso 1: Abrir pgAdmin 4 y Conectarse al Servidor:**
- Inicia pgAdmin 4 desde el menú de inicio de Windows.
- Conéctate al servidor PostgreSQL:
   - En el panel izquierdo, haz clic derecho en "Servers" y selecciona "Create" -> "Server..."
   - En la pestaña "General", ingresa un nombre para el servidor.
   - En la pestaña "Connection", ingresa los detalles de conexión.
   - Haz clic en "Save".
 
**Paso 2: Crear un Nuevo Esquema:** 
- Expande el servidor conectado y luego la base de datos predeterminada.
- Haz clic derecho en "Schemas" y selecciona "Create" -> "Schema...".
- En la ventana emergente, ingresa el nombre del esquema (por ejemplo, `empresa`) y haz clic en "Save".

**Paso 3: Crear Tablas:**
- Expande el esquema `empresa`, luego haz clic derecho en "Tables" y selecciona "Create" -> "Table...".
- En la pestaña "General", ingresa el nombre de la tabla (`departamentos`).
- En la pestaña "Columns", define las columnas:
   - **id**: SERIAL, Primary Key.
   - **nombre**: VARCHAR(100), Not NULL.
   - **ubicacion**: VARCHAR(100)
- Haz clic en "Save".
- Repite el proceso para crear la tabla `empleados` con las siguientes columnas:
   - **id**: SERIAL, Primary Key.
   - **nombre**: VARCHAR(100), Not NULL.
   - **puesto**: VARCHAR(100), Not NULL.
   - **salario**: NUMERIC, Check (salario > 0).
   - **departamento_id**: INTEGER, Foreign Key (References departamentos (id)).
   - Haz clic en "Save".
  

</details>



### 🤓 Proyecto Modular

<details>
<summary style= "background: ghostwhite; padding: 10px; border: 1px solid lightgray; margin: 0px;"><strong>Configuración del entorno SQL</strong><br/></summary>
<br/>

Con el fin de que puedas poner todo tu conocimiento en práctica a lo largo de este módulo se realizarán distintas actividades que te permitirán ir construyendo un proyecto de manera progresiva y de manera guiada por los expertos. Este proyecto será el entregable final de todo del módulo y se dividirá en las siguientes etapas:

- [x] Creación de un repositorio   
- [x] Obtención de datos   
- [ ] Configuración del entorno SQL   
- [ ] Diseño de la base de datos
- [ ] Gestión de usuarios
- [ ] Creando una copia de seguridad
- [ ] Optimizando consultas
- [ ] Preparando un proceso de réplica y alta disponibilidad
- [ ] Preparando el monitoreo
- [ ] Migración de datos
- [ ] Presentación del proyecto

---
 
#### :dart: Avance del Proyecto 3/10: Configuración del entorno SQL

En esta tercera sesión te orientaremos en la configuración del entorno SQL para tu proyecto, con el fin de que puedas experimentar con algunas de las principales características de PostgreSQL.  

⏰ Tiempo estimado: *60 minutos*

1. Replicando el hands-on que revisamos durante la sesión, asegurate de tener todo configurado para cargar los datos de tu base. No te preocupes mucho por el diseño de momento, ya lo mejoraremos en la siguiente sesión.

</details>

[`< Regresar`](../README.md)
