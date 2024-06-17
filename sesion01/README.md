[`PostgreSQL Avanzado`](../README.md)

## Sesión 01: Introducción a PostgreSQL

### 🌿 Presentación 

Esta sesión ofrece una visión general de PostgreSQL, su origen y desarrollo a lo largo del tiempo. Se analizarán características y ventajas que lo hacen destacar frente a otros sistemas de gestión de bases de datos, además de explorar los diferentes casos de uso en diversos sectores.

### 🎯 Objetivo

Comprender la historia, evolución y cacterísticas principales de PostgreSQL así como identificar sus principales casos de uso y ventajas.

### 🤓 Proyecto Modular

<details>
<summary style= "background: ghostwhite; padding: 10px; border: 1px solid lightgray; margin: 0px;"><strong>Creación de un Repositorio</strong><br/></summary>
<br/>

Con el fin de que puedas poner todo tu conocimiento en práctica a lo largo de este módulo se realizarán distintas actividades que te permitirán ir construyendo un proyecto de manera progresiva y de manera guiada por los expertos. Este proyecto será el entregable final de todo del módulo y se dividirá en las siguientes etapas:

- [ ] Creación de un repositorio   
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
 
#### :dart: Avance del Proyecto 1/10: Creación de un repositorio

En esta primera sesión te orientaremos en la creación de un repositorio para que puedas alojar tu proyecto y lo presentes en la sesión final del módulo. 

⏰ Tiempo estimado: *60 minutos*

**Paso 1: Configura una cuenta en GitHub en caso de que no tengas una**

1. Ingresa a la página [https://github.com/](https://github.com/).

   ![img](imagenes/img01.png)

2. Da clic en el botón que se encuentra en la esquina superior derecha `Sign Up`.

   ![img](imagenes/img02.png)

3. Coloca los datos que se solicitan y ve presionando el botón `Continue`.

   ![img](imagenes/img03.png)

   ![img](imagenes/img04.png)

   ![img](imagenes/img05.png)

   ![img](imagenes/img06.png)

4. Verifica tu cuenta resolviendo el acertijo.

   ![img](imagenes/img07.png)

5. Se enviará un correo a tu cuenta para confirmala, coloca el código.

   ![img](imagenes/img08.png)

6. Inicia sesión con los datos que acabas de configurar.

   ![img](imagenes/img09.png)

7. Contesta la encuesta de inicio o elige `Skip personalization`

   ![img](imagenes/img10.png)

**¡Con esto tienes tu cuenta lista!**


**Paso 2: Instala Git en tu computadora**

1. Ingresa a la página [https://www.git-scm.com/downloads](https://www.git-scm.com/downloads).

   ![img](imagenes/img11.png)

2. Elige tu sistema operativo y sigue el tutorial según corresponda.

   ![img](imagenes/img12.png)

**Paso 3: Crea una estructura de carpetas en tu equipo**


Configura en tu equipo una estructura de carpetas, donde desees colocar el proyecto. En esta estructura se irán creando las soluciones a las distintas actividades que realizaremos a lo largo del módulo, de momento, la estructura de tu carpeta queda libre, pero poco a poco iremos estandarizando su contenido.


**Paso 4: Añade un archivo `README.md` en blanco**


Dentro de la siguiente [liga](plantilla/README.md) encontrarás un documento en formato **Markdown** puedes utilizarlo para ir generando una pequeña documentación sobre tu proyecto. De momento basta con que coloques datos básicos y lo iremos completando poco a poco a lo largo del resto de sesiones.

Adicionalmente te dejamos la documentación de **Markdown** para que aprendas un poco más de este lenguaje de marcado:

🔗 [Sintaxis de escritura y formato básicos
](https://docs.github.com/es/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)



**Paso 5: Empuja (`push`) los datos al repositorio de GitHub**

Para poder realizar `push` en un repositorio de GitHub, necesitamos primero contar con un *token* de acceso, para obtenerlo dirígete a la página: [https://github.com/settings/tokens](https://github.com/settings/tokens).

Una vez configurado el *token*, usa la terminal de Git para dirigirte a la ruta de carpetas que configuraste. Para subir tus cambios siempre deberás colocar los siguientes comandos:

*Agregar los archivos modificados*

```bash
> git add .
```

*Confirmar los cambios*

```bash
> git commit -m "Primer commit"
```

*Empujar los cambios*

```bash
> git push origin main
```

Una vez hecho esto, puedes ingresar 


---

#### :rocket: Tu avance: <progress max="100" value="9">9%</progress>

- [x] Creación de un repositorio 

---

</details>

[`< Regresar`](../README.md)
