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
