[`PostgreSQL Avanzado`](../../../README.md) > [`Sesión 06`](../../README.md) > [`Círculo de estudio`](../README.md)

#### Reto 3

##### Objetivos 🎯

- Poner en práctica la creación de tablas en **SQL**.

##### Requisitos 📋

- MySQL Workbench instalado.

##### Desarrollo 🚀

Vayamos a la primera parte de la solución: 

*Cargar los datos del archivo en las tablas que creaste. Esto lo puedes hacer con `INSERT INTO` (aunque son 50 registros, no creemos que seas tan paciente...), con el comando `LOAD DATA INFILE` o bien usando el asistente de PgAdmin 4 (liga del tutorial: [aquí](https://www.pgadmin.org/docs/pgadmin4/latest/import_export_data.html)).*

Te sugerimos seguir los siguientes pasos para llegar a la solución. Sin embargo, puedes resolverlo de la forma que creas más conveniente:

---
> **Paso 1.** Cargar los datos.
>
> <details><summary>Solución</summary>
>
> 1. Guardar cada hoja como un archivo CSV. Para ello vamos a `Archivo` > `Exportar` y seleccionamos *Descargar esta hoja como CSV*. Si no te sale esa opción esto dependerá de la versión del software para manejar hojas de cálculo. Pregunta a **ChatGPT** o a tu experta o experto.
>
>   Te dejamos los archivos por cualquier cosa:
>
>    - [Alumnos.csv](../../archivos/Alumnos.csv)
>    - [Tareas.csv](../../archivos/Tareas.csv)
>    - [Examenes.csv](../../archivos/Examenes.csv)
>
> 2. Te mostraremos cómo cargar el archivo `Alumnos.csv` y te dejaremos a ti cargar los otros. En el listado de tablas que muestra PgAdmin 4, da clic derecho sobre el nombre de la tabla que quieras cargar y selecciona "Import/Export data"
>
>    ![img](../../imagenes/img05.png)
> 
> 
> 3. Busca tu archivo y da clic en Ok. 
>
> ![img](../../imagenes/img06.png)
>
> 4. Al finalizar nos indicará que cargó los 50 registros, cosa que podemos verificar haciendo un bonito `SELECT`.
>
> ![img](../../imagenes/img07.png)
>
> ```sql
> SELECT *
> FROM public."Alumnos";
> ```
> **Te toca cargar el resto de tablas, las necesitamos todas para el siguiente reto**.
> </details>
---

[`Anterior`](../reto02/README.md) | [`Siguiente`](../reto04/README.md)
