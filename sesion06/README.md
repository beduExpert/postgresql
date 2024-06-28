[`PostgreSQL Avanzado`](../README.md)

## Sesión 06: Copias de Seguridad y Recuperación

### 🌿 Presentación 

En esta sesión aprenderemos cómo realizar copias de seguridad y restaurar bases de datos en **PostgreSQL**. Se cubrirán métodos lógicos y físicos de *backup*, así como estrategias de recuperación ante desastes y recuperación e un punto en el tiempo (PITR).

### 🎯 Objetivo

Implementar estategias efectivas de copia de seguridad y recuperación para garantizar la integridad y disponibilidad de los datos en **PostgreSQL**.

### 🧠 Círculo de estudio

*En esta sesión tendremos un pequeño círculo de estudio para asegurarnos que no tengas dudas sobre los contenidos previos. No dudes en expresar cualquier duda que tengas*

- [Diseño de una base de datos para calificaciones](circulo_estudio/README.md)

### 📚 Contenido

En **PostgreSQL**, existen dos tipos principales de copias de seguridad: la copia de seguridad lógica y la copia de seguridad física. Cada una tiene sus propios usos, ventajas y limitaciones. A continuación se detallan las diferencias clave entre ambas.

- [6.1. Copia de Seguridad Lógica](tema01/README.md)
- [6.2. Copia de Seguridad Física](tema02/README.md)
- [6.3. Restauración de Datos](tema03/ejemplo02/README.md)
- [6.4. Estrategias de Recuperación](tema04/README.md)
- [6.5. Conclusión](tema05/README.md)

### 🤓 Proyecto Modular

---

<details><summary><h3>Creando una copia de seguridad</h3></summary>
<br/>

Con el fin de que puedas poner todo tu conocimiento en práctica a lo largo de este módulo se realizarán distintas actividades que te permitirán ir construyendo un proyecto de manera progresiva y de manera guiada por los expertos. Este proyecto será el entregable final de todo del módulo y se dividirá en las siguientes etapas:

- [x] Creación de un repositorio   
- [x] Obtención de datos   
- [x] Configuración del entorno SQL   
- [x] Diseño de la base de datos
- [x] Gestión de usuarios
- [ ] Creando una copia de seguridad
- [ ] Optimizando consultas
- [ ] Preparando un proceso de réplica y alta disponibilidad
- [ ] Preparando el monitoreo
- [ ] Migración de datos
- [ ] Presentación del proyecto

---
 
#### :dart: Avance del Proyecto 6/10: Creando una copia de seguridad

##### Actividad

⏰ Tiempo estimado: *60 minutos*

1. **Utilizar pg_dump para crear una copia de seguridad**:

  - Ejecuta pg_dump para crear un backups de la base de datos.

2. **Guardar el archivo de copia de seguridad en la carpeta `backup`**:

  - Asegúrate de que la carpeta `backup` esté en tu repositorio.

**Ejemplo**:

```sh
pg_dump -U postgres proyecto_db > backup/proyecto_db_backup.sql
```

</details>

---

[`< Regresar`](../README.md)
