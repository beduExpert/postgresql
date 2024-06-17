[`PostgreSQL Avanzado`](../README.md)

## Sesión 03: Herramientas y Utilidades (PSQL y PgAdmin4)

### 🌿 Presentación 

Esta sesión te guiará a través del proceso de instalación y configuración de PostgreSQL y PgAdmin4. Además, te enseñaremos el uso de PSQL, la interfaz de línea de comandos, y PgAdmin4, una herramientas gráfica de administración para realizar tareas básicas y avanzadas.

### 🎯 Objetivo

Instalar y configurar PostgreSQL y PgAdmin4, y aprender a utilizar las herramientas básicas para la administración y ejecución de comandos SQL.

### 👨‍💻 Hands-on para iniciar

<details>
<summary style= "background: ghostwhite; padding: 10px; border: 1px solid lightgray; margin: 0px;"><strong>Instalaciones</strong><br/></summary>
<br/>

#### Objetivo
Instalar PostgreSQL 16 y pgAdmin4 en un sistema operativo Windows de manera correcta y configurar las bases de datos básicas.

#### Materiales Necesarios:
- Computadora con sistema operativa Windows (versión 7 en adelante).
- Conexión a Internet
- Permisos de administración en el sistema.

#### Tiempo Estimado: 
30-45 minutos.

#### Instrucciones paso a paso

1. Abrir el navegador:
   - Abre tu navegador de preferencia (Chrome, Firefox, Edge, etc.).
  
2. Ir a la página oficinal:
   - Navega a la página oficial de PostgreSQL:   
      [https://www.postgresql.org/download/windows/](https://www.postgresql.org/download/windows/)

3. Seleccionar la versión:
   - En la sección de descarga para Windows, selecciona PostgreSQL 16.

5. Descargar el instalador:
   - Haz clic en el botón de descarga y selecciona el instalador para Windows (x86-64).
   - Guarda el archivo en una ubicación de fácil acceso en tu computadora.
 
6. Ejecutar el instalador:
   - Navega hasta la ubicación donde descargaste el archivo y haz doble clic en el instalador (`postgresql-16.x-windows-x64.exe`).
  
7. Iniciar el proceso de instalación:
   - En la ventana de bienvenida, haz clic en "Next" (Siguiente).
  
8. Seleccionar la ruta de instalación:
   - Elige la ubicación donde deseas instalar PostgreSQL (por defecto es `C:\Program Files\PostgreSQL\16`).
   - Haz clic en "Next" (Siguiente).
  
9. Seleccionar componentes:
   - Deja seleccionados todos los componentes necesarios por PostgreSQL.
   - Si pgAdmin no está incluido, procede sin seleccionarlo. Lo instalaremos en otro paso.
   - Haz clic en "Next" (Siguiente).
  
10. Elegir directorio de datos:
   - Elige la ubicación del directorio de datos donde PostgreSQL almacenará las bases de datos (por defecto es `C:\Program Files\PostgreSQL\16\data`).
   - Haz clic en "Next" (Siguiente).

11. Configurar constraseña del Superusuario (postgres):
   - Ingresa una constraseña segura para el usuario `postgres`.
   - Confirma la contraseña y haz clic en "Next" (Siguiente).

12. Configurar puerto:
   - El puerto por defecto es `5432`. Puedes dejarlo así a menos que necesites cambiarlo.
   - Haz clic en "Next" (Siguiente)

13. Seleccionar región y codificación
   - Deja las opciones por defecto (región en `default` y codificación en `UTF-8`).
   - Haz clic en "Next" (Siguiente).

14. Finalizar la instalación
   - Revisa la configuración y haz clic en "Next" (Siguiente) y luego en "Finish" (Finalizar).

15. Ir a la página de descargas de pgAdmin:
   - Navega a la página de descarga de pgAdmin: [https://www.pgadmin.org/download/](https://www.pgadmin.org/download/).

16. Seleccionar la versión de Windows:
   - Haz clic en la opción para descargar pgAdmin para Windows.

17. Descargar el instalador:
   - Descarga el instalador de pgAdmin 4 y guarda el archivo en una ubicación de fácil acceso en tu computadora.

18. Ejecutar el instalador:
   - Navega hasta la ubicación donde descargaste el archivo y haz doble clic en el instalador (`pgadmin4-x.x-x86.exe`).

19. Iniciar el proceso de instalación:
   - En la ventana de bienvenida, haz cic en "Next" (Siguiente).

20. Aceptar el acuerdo de licencia:
   - Lee y acepta el acuerdo de licencia, luego haz clic en "Next" (Siguiente).

21. Seleccionar la ruta de instalación:
   - Elige la ubicación donde deseas instalar pgAdmin 4 (por defecto es `C:\Program Files\pgAdmin 4`).
   - Haz clic en "Next" (Siguiente).

22. Seleccionar el tipo de instalación:
   - Elige "Full" (Completa) para instalación instalar todas las características de pgAdmin 4.
   - Haz clic en "Next" (Siguiente)

23. Finalizar la instalación:
   - Revisa la configuración y haz clic en "Install" (Instalar).
   - Una vez completada la instalación, haz clic en "Finish" (Finalizar).

24. Abrir pgAdmin 4:
   - Ve al menú de inicio de Windows y busca `pgAdmin 4`.
   - Abre la aplicación pgAdmin 4.

25. Conectar al servidor:
   - En pgAdmin 4, haz clic en "Servers" y luego "PostgreSQL 16".
   - Ingresa la contraseña del usuario `postgres` que configuraste durante la instalación de PostgreSQL.

26. Crear una base de datos de prueba:
   - Haz clic derecho en `Databases` y selecciona `Create -> Database`.
   - Ingresa un nombre para tu nueva base de datos y haz clic en `Save`.

27. Verifica la base de datos:
   - Expande el nodo de `Databases` para ver tu nueva base de datos y asegúrate de que esté listada correctamente.

¡Felicidades! Ahora tienes PostgreSQL 16 y pgAdmin 4 instalados y configurados en tu sistema Windows. Puedes comenzar a crear y gestionar tus bases de datos utilizando pgAdmin 4 u otras herramientas de tu preferencia.

</details>

<details>
<summary style= "background: ghostwhite; padding: 10px; border: 1px solid lightgray; margin: 0px;"><strong>Comandos básicos PSQL</strong><br/></summary>
<br/>

#### Objetivo:
Aprender a usar PSQL para gestionar bases de datos PostgreSQL mediante comandos básicos y avanzados.

#### Materiales necesarios:
- PostgreSQL 16 instalado en tu sistema Windows.
- Acceso a una terminal o línea de comandos
- Conexión a Internet (opcional para consultar documentación).

#### Tiempo estimado:
45-60 minutos.

#### Instrucciones paso a paso

1. Abril la terminal o línea de comandos
   - Abre `cmd` o `PowerShell`

2. Conectar a PostgreSQL con PSQL
   - Ejecuta el siguiente comando reemplazando `username` con tu nombre de usuario PostgreSQL y `dbname` con el nombre de la base de datos a la que quieras conectarte:
      ```sql
      psql -U username -d dbname
      ```

   - Si estás utilizando la base de datos `postgres` y el usuario `postgres`, el comando sería:
      ```sql
      psql -U postgres -d postgres
      ```

3. Ingresar la contraseña:
   - Se te pedirá que ingreses la contraseña del usuario `postgres`. Escríbela y presiona `Enter`.

4. Listar bases de datos:
   - Para ver todas las bases de datos disponibles, usa:
      ```sql
      \l
      ```
5. Conectarse a una base de datos:
   - Para cambiar a otra base de datos, usa:
     ```sql
     \c dbname
     ```

6. Listar tablas:
   - Para ver todas las tablas en la base de datos actual, usa:
      ```sql
      \dt
      ```

7. Salir de PSQL:
   - Para salir del cliente PSQL usa:
      ```sql
      \q
      ```

8. Crear una tabla:
   - Crear una tabla simple llamada `empleados`:
      ```sql
      CREATE TABLE empleados (
         id SERIAL PRIMARY KEY,
         nombre VARCHAR(100),
         puesto VARCHAR(100),
         salario NUMERIC
      );
      ```

9. Insertar datos en la tabla `empleados`:
   ```sql
   INSERT INTO empleados (nombre, puesto, salario) VALUES 
   ('Juan Pérez', 'Gerente', 50000),
   ('Ana Gómez', 'Desarrollador', 40000),
   ('Luis García', 'Diseñador', 35000);
   ```

10. Consultar todos los registros de la tabla `empleados`:
   ```sql
   SELECT * FROM empleados;
   ```

11. Actualizar el salario de un empleado:
   ```sql
   UPDATE empleados SET salario = 45000 WHERE nombre = 'Ana Gómez';
   ```

12. Eliminar un registro de la tabla `empleados`:
   ```sql
   DELETE FROM empleados WHERE nombre = 'Luis Garcia';
   ```

13. Ver la estructura de la tabla `empleados`:
   ```sql
   \d empleados
   ```

14. Exportar los datos de `empleados`a un archivo CSV:
   ```sql
    \COPY empleados TO 'empleados.csv' CSV HEADER;
   ```

15. Importar datos desde un archivo CSV a la tabla `empleados`:
   ```sql
   \COPY empleados FROM 'empleados.csv' CSV HEADER;
   ```

16. Iniciar una transacción, realizar cambios y confirmar:
   ```sql
   BEGIN;
   INSERT INTO empleados (nombre, puesto, salario) VALUES ('Carlos Ruiz', 'Analista', 42000);
   COMMIT;
   ```

17. Obtener ayuda sobre los comandos disponibles:
   ```sql
   \?
   ```

18. Ver las variables de configuración actuales:
   ```sql
   SHOW ALL;
   ``

19. Ejecutar comandos SQL desde un archivo:
   ```sql
   \i ruta/al/archivo.sql
   ```

#### Conclusión
¡Felicidades! Ahora sabes cómo utilizar PSQL para gestionar bases de datos PostgreSQL. Has aprendido a conectarte, navegar, crear tablas, insertar y consultar datos, y utilizar comandos avanzados. Practica estos comandos regularmente para mejorar tu habilidad con PSQL y gestionar tus bases de datos de manera eficiente.

</details>

<details>
<summary style= "background: ghostwhite; padding: 10px; border: 1px solid lightgray; margin: 0px;"><strong>Uso básico de pgAdmin 4</strong><br/></summary>
<br/>

#### Objetivo
Aprender a usar pgAdmin 4 para gestionar bases de datos PostgreSQL mediante la interfaz gráfica.

#### Materiales Necesarios
- PostgreSQL 16 y pgAdmin 4 instalados en tu sistema Windows
- Conexión a Internet (opcional para consultar documentación)

#### Tiempo Estimado:
45-60 minutos.

#### Instrucciones pasos a paso

1. Abrir pgAdmin 4:
   - Inicia pgAdmin 4 desde el menú de inicio de Windows.
  
2. Conectarse al servidor PostgreSQL:
   - En el panel izquierdo, haz clic derecho en "Servers" y selecciona "Create" -> "Server...".
   - En la pestaña "General", ingresa un nombre para el servidor (por ejemplo, `PostgreSQL16`).
   - En la pestaña "Connection",, ingresa los detalles de conexión:
      - **Host name/address: `localhost`**
      - **Port: `5432`**
      - **Username: `postgres`**
      - **Password:** ingresa la contraseña que configuraste durante la instalación.
   - Haz clic en "Save" para conectar.
  
3. Crear una nueva base de datos:
   - En el panel izquierdo, expande el servidor que acabas de crear.
   - Haz clic derecho en "Databases" y selecciona "Create" -> "Database...".
   - En la ventana emergente, ingresa el nombre de la base de datos (por ejemplo `empresa`).
   - Haz clic en "Save".
  
4. Crear tabla `departamentos`:
   - Expande la base de datos `empresa`, luego expande "Schemas" -> "public" -> "Tables".
   - Haz clic derecho en "Tables" y  selecciona "Create" -> "Table..."
   - En la pestaña "General", ingresa el nombre de la tabla (`departamentos`).
   - En la pestaña "Columns", define las columnas:
      - **id**: SERIAL, Primary Key.
      - **nombre:** VARCHAR(100), NOT NULL.
      - **ubicacion:** VARCHAR(100).
   - Haz clic en "Save".
  
5. Crear tabla `empleados`:
   - Repite los pasos anteriores para crear la tabla `empleados` con las siguientes columnas:
      - **id:** SERIAL, Primary Key.
      - **nombre:** VARCHAR(100), Not NULL.
      - **puesto:** VARCHAR(100), Not NULL.
      - **salario:** NUMERIC, Check (salario > 0).
      - **departamento_id**: INTEGER, Foreign Key (References departamentosd(id)).
    
6. Insertar Datos en `departamentos`:
   - En el panel izquierdo, expander la tabla `departamentos`.
   - Haz clic derecho en "Query Tool" y usa el siguiente comando para insertar datos:
      ```sql
      INSERT INTO departamentos (nombre, ubicacion) VALUES 
      ('Recursos Humanos', 'Edificio A'),
      ('Tecnología', 'Edificio B'),
      ('Ventas', 'Edificio C');
      ```

7. Insertar Datos en `empleados`:
   - Repite el proceso en la tabla `empleados` con el siguiente comando:
      ```sql
      INSERT INTO empleados (nombre, puesto, salario, departamento_id) VALUES 
      ('Juan Pérez', 'Gerente', 50000, 1),
      ('Ana Gómez', 'Desarrollador', 40000, 2),
      ('Luis García', 'Vendedor', 35000, 3);
      ```

8. Consultar datos de `empleados`:
   - Abre la "Query Tool" para la tabla `empleados`y ejecuta el siguiente comando:
      ```sql
      SELECT * FROM empleados;
      ```
9. Unir tablas `empleados` y `departamentos`:
   - En la "Query Tool", ejecuta el siguiente comando para ver los empleados junto con sus departamentos:
      ```sql
      SELECT e.nombre AS empleado, e.puesto, e.salario, d.nombre AS departamento, d.ubicacion
      FROM empleados e
      JOIN departamentos d ON e.departamento_id = d.id;
      ```

10. Agregar una columna a `empleados`:
   - En la tabla `empleados`, haz clic derecho y selecciona "Properties".
   - En la pestaña "Columns", agrega una nueva columna `fecha_contractacion` de tipo `DATE`.
   - Haz clic en "Save".

11. Actualizar datos de `empleados`:
   - En la "Query Tool", ejecuta los siguientes comandos para actualizar las fechas de contratación:
      ```sql
      UPDATE empleados SET fecha_contratacion = '2023-01-15' WHERE nombre = 'Juan Pérez';
      UPDATE empleados SET fecha_contratacion = '2023-02-20' WHERE nombre = 'Ana Gómez';
      UPDATE empleados SET fecha_contratacion = '2023-03-05' WHERE nombre = 'Luis García';
      ```

12. Iniciar una transacción:
   - En la "Query Tool", ejecuta el siguiente comando: 
      ```sql
      BEGIN;
      ```

13. Realizar operaciones:
   - Inserta un nuevo empleado:
      ```sql
      INSERT INTO empleados (nombre, puesto, salario, departamento_id, fecha_contratacion) VALUES ('Carlos Ruiz', 'Analista', 42000, 1, '2023-04-01');
      ```

   - Si decides deshacer la transacción:
      ```sql
      ROLLBACK;
      ```

14. Configrmar transacción:
   - Si todo está correcto:
      ```sql
      COMMIT;
      ```

15. Crear una vista para empleados y departamentos:
   - En la "Query Tool", ejecuta el siguiente comando:
      ```sql
      CREATE VIEW vista_empleados_departamentos AS
      SELECT e.nombre AS empleado, e.puesto, e.salario, d.nombre AS departamento, d.ubicacion
      FROM empleados e
      JOIN departamentos d ON e.departamento_id = d.id;
      ```

16. Consultar la vista:
   - Consulta la vista creada:
      ```sql
      SELECT * FROM vista_empleados_departamentos;
      ```

#### Conclusión:
¡Felicidades! Ahora sabes cómo utilizar pgAdmin 4 para gestionar bases de datos PostgreSQL. Has aprendido a conectarte, crear bases de datos y tablas, insertar y consultar datos, modificar el diseño de la base de datos y utilizar transacciones para asegurar la integridad. Practica estos pasos regularmente para mejorar tu habilidad con pgAdmin 4 y gestionar tus bases de datos de manera eficiente.

</details>


### 🤓 Proyecto Modular

<details>
<summary style= "background: ghostwhite; padding: 10px; border: 1px solid lightgray; margin: 0px;"><strong>Obtención de datos</strong><br/></summary>
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
 
#### :dart: Avance del Proyecto 2/10: Obtención de datos

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

[`< Regresar`](../README.md)
