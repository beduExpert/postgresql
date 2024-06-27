[`PostgreSQL Avanzado`](../README.md)

# Sesión 02: Arquitectura y Componentes Internos de PostgreSQL

## 🌿 Introducción

Comprender la arquitectura y los componentes internos de PostgreSQL es esencial para aprovechar al máximo sus capacidades y optimizar su rendimiento. Esta sesión explorará la estructura general del servidor PostgreSQL, los procesos internos y subsistemas, y la organización de datos. Adquirirás una comprensión profunda de cómo funciona PostgreSQL internamente, lo que te permitirá realizar tareas de administración, optimización y resolución de problemas de manera más eficaz.

## 🎯 Objetivos Generales

1. Comprender la estructura general del servidor PostgreSQL y las bases de datos.
2. Conocer los procesos internos y subsistemas que constituyen PostgreSQL.
3. Aprender sobre la organización de datos en PostgreSQL y su impacto en el rendimiento y la administración.

## 📚 Temario

1. **Estructura General**
      - Servidor PostgreSQL
      - Bases de datos

2. **Proceso Interno y Subsistemas**
      - Procesos del servidor (postmaster, backends, autovacuum, etc.)
      - Módulos de almacenamiento y recuperación

3. **Organización de Datos**
      - Tabla
      - Índice
      - Esquema
      - Espacio de tablas

## 🚀 Desarrollo

---

<details><summary><h3>Estructura General</h3></summary>
<br/>

#### Servidor PostgreSQL

El servidor PostgreSQL es el núcleo del sistema de gestión de bases de datos. Comprender su estructura general es crucial para administrar y optimizar PostgreSQL.

- **Componentes del Servidor**: 
  - PostgreSQL se compone de un conjunto de procesos del servidor que se encargan de aceptar conexiones, ejecutar consultas y realizar tareas de mantenimiento.
  - **Postmaster**: El proceso principal del servidor que inicia y gestiona otros procesos de PostgreSQL.

#### Bases de Datos

En PostgreSQL, una instancia del servidor puede contener múltiples bases de datos, cada una con sus propios esquemas y datos.

- **Instancia y Bases de Datos**: 
  - Una instancia de PostgreSQL puede alojar múltiples bases de datos independientes.
  - Cada base de datos tiene su propio conjunto de esquemas, tablas, índices y otros objetos.


<br/>
</details>

---

<details><summary><h3>Proceso Interno y Subsistemas</h3></summary>
<br/>

#### Procesos del Servidor (postmaster, backends, autovacuum, etc.)

PostgreSQL utiliza varios procesos internos para manejar las operaciones del servidor y mantener la base de datos en funcionamiento óptimo.

- **Postmaster**: Proceso principal que gestiona la creación de otros procesos y maneja las conexiones de los clientes.
- **Backends**: Procesos de servidor dedicados a manejar conexiones individuales de clientes.
- **Autovacuum**: Proceso que automatiza la tarea de VACUUM para mantener la base de datos optimizada.

#### Módulos de Almacenamiento y Recuperación

PostgreSQL tiene subsistemas dedicados al almacenamiento y recuperación de datos, garantizando la integridad y eficiencia del acceso a los datos.

- **WAL (Write-Ahead Logging)**: Mecanismo que asegura la durabilidad y recuperación de transacciones.
- **Sistema de Archivos**: PostgreSQL utiliza el sistema de archivos del sistema operativo para almacenar datos.
- **Subsistema de Recuperación**: Módulo encargado de la recuperación de datos en caso de fallos.



<br/>
</details>

---

<details><summary><h3>Organización de Datos</h3></summary>
<br/>

#### Tabla

Las tablas son el componente básico del almacenamiento de datos en PostgreSQL. Comprender su estructura y funcionamiento es fundamental para la administración y optimización.

- **Filas y Columnas**: Cada tabla está compuesta por filas (registros) y columnas (atributos).
- **Particionamiento de Tablas**: Técnica para dividir tablas grandes en partes más manejables y mejorar el rendimiento.

#### Índice

Los índices son estructuras de datos que mejoran la velocidad de acceso a los datos. Conocer cómo funcionan y cómo se administran 

- **Tipos de Índices**: B-tree, Hash, GiST, GIN, entre otros.
- **Mantenimiento de Índices**: Operaciones de REINDEX y VACUUM para mantener índices eficientes.

#### Esquema

Los esquemas proporcionan una forma de organizar y agrupar objetos de base de datos. Comprender su uso y gestión es importante para la administración de bases de datos complejas.

- **Definición de Esquemas**: Espacios de nombres que contienen tablas, vistas, índices y otros objetos.
- **Gestión de Esquemas**: Creación, modificación y eliminación de esquemas.

#### Espacio de Tablas

Los espacios de tablas permiten a los administradores de bases de datos definir ubicaciones específicas en el sistema de archivos para almacenar datos.

- **Definición de Espacios de Tablas**: Áreas en el sistema de archivos donde se almacenan objetos de base de datos.
- **Gestión de Espacios de Tablas**: Crear, modificar y eliminar espacios de tablas.


<br/>
</details>

---

### 💯 Conclusión

Conocer la arquitectura y los componentes internos de PostgreSQL es esencial para administrar y optimizar el rendimiento de las bases de datos. Esta sesión ha proporcionado una visión profunda de la estructura general del servidor, los procesos internos y subsistemas, y la organización de datos en PostgreSQL. Con esta comprensión, los administradores de bases de datos estarán mejor equipados para gestionar, optimizar y resolver problemas en sus entornos de PostgreSQL.

### 🤓 Proyecto Modular

---

<details><summary><h3>Obtención de Datos</h3></summary>
<br/>

Con el fin de que puedas poner todo tu conocimiento en práctica a lo largo de este módulo se realizarán distintas actividades que te permitirán ir construyendo un proyecto de manera progresiva y de manera guiada por los expertos. Este proyecto será el entregable final de todo del módulo y se dividirá en las siguientes etapas:

- [x] Creación de un repositorio   
- [ ] Obtención de datos   
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
 
#### :dart: Avance del Proyecto 2/10: Obtención de Datos

En esta segunda sesión te orientaremos en la obtención de datos para tu proyecto, con el fin de que puedas experimentar con algunas de las principales características de PostgreSQL.  

⏰ Tiempo estimado: *60 minutos*

1. Puedes trabajar en una amplia variedad de proyectos que aborden probemas del mundo real. Basado en esto te damos algunas ideas de proyectos, puedes adaptarlos a tus intereses.

   - Sistema de Gestión de Hospitales
   - Plataforma de E-commerce
   - Red Social para Profesionales
   - Gestión de Reservas de Hoteles
   - Sistema de Inventario para Tiendas
   - Portal de Publicación de Artículos Científicos
   - Aplicación de Seguimiento de Fitness
   - Sistema de Gestión de Proyectos
   - Base de Datos para una Biblioteca
   - Aplicación de Encuestas y Análisis de Datos
   - Sistema de Gestión de Empleados
   - Plataforma de Cursos Online
   - Sistema de Seguimiento de Ventas y Clientes
   - Portal de Noticias con Gestión de Usuarios
   - Aplicación de Gestión de Finanzas Personales
   - Sistema de Reservas de Restaurantes
   - Gestión de Eventos y Conferencias
   - Aplicación de Seguimiento de Tareas y Productividad
   - Sistema de Gestión de Flotas de Vehículos
   - Plataforma de Crowdfunding

2. Las ideas del punto anterior son el objetivo final del módulo. La idea es que puedas modelar la base de datos que usarás en tu proyecto.

3. Existen varias fuentes de datos de donde puedes extraer datos de manera gratuita. También puedes usar conjuntos de datos que tengas de tu trabajo o algún proyecto personal. Te recomendamos las siguientes plataformas:

   - https://www.kaggle.com/
   - https://datos.cdmx.gob.mx/
   - https://datos.gob.mx/
   - https://datos.bancomundial.org/

4. Como sugerencia busca conjuntos de datos que tengan una amplia gama de registros, no te quedes con conjuntos pequeños.


</details>

---

[`< Regresar`](../README.md)
