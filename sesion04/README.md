[`PostgreSQL Avanzado`](../README.md)

# Sesión 04: Diseño de Bases de Datos en PostgreSQL

## 🌿 Introducción

El diseño eficiente de bases de datos es crucial para el rendimiento y la funcionalidad de las aplicaciones que las utilizan. Este curso avanzado de PostgreSQL se centra en el diseño de bases de datos, cubriendo desde el modelado de datos y la creación de esquemas hasta la implementación de relaciones, llaves y el uso de índices y vistas. Adquirirás habilidades avanzadas para diseñar y optimizar bases de datos en PostgreSQL, asegurando una estructura robusta y un acceso eficiente a los datos.

## 🎯 Objetivos Generales

1. Aprender a modelar datos y crear esquemas y tablas en PostgreSQL.
2. Comprender y aplicar relaciones y llaves para mantener la integridad referencial.
3. Conocer y utilizar índices y vistas para optimizar el rendimiento de las consultas.

## 📚 Temario

### Temario

1. **Modelado de Datos**
      - Creación de esquemas y tablas
      - Tipos de datos disponibles

2. **Relaciones y Llaves**
      - Llaves primarias y foráneas
      - Integridad referencial

3. **Índices y Vistas**
      - Tipos de índices y su uso
      - Creación y uso de vistas

## 🚀 Desarrollo

---

<details><summary><h3>Modelado de Datos</h3></summary>
<br/>

#### Creación de Esquemas y Tablas

El modelado de datos comienza con la creación de esquemas y tablas, que son la base de cualquier base de datos relacional. PostgreSQL ofrece una amplia gama de funcionalidades para definir estructuras de datos.

- **Esquemas**: Espacios de nombres que permiten organizar objetos de base de datos.
  ```sql
  CREATE SCHEMA mi_esquema;
  ```
- **Tablas**: Estructuras básicas para almacenar datos.
  ```sql
  CREATE TABLE mi_esquema.mi_tabla (
    id SERIAL PRIMARY KEY,
    nombre VARCHAR(100),
    edad INT
  );
  ```

#### Tipos de Datos Disponibles

PostgreSQL ofrece una gran variedad de tipos de datos que permiten definir con precisión los atributos de las tablas.

- **Tipos de Datos Comunes**: 
  - `INTEGER`, `SERIAL`, `BIGINT`
  - `VARCHAR`, `TEXT`
  - `DATE`, `TIMESTAMP`
  - `BOOLEAN`
- **Tipos de Datos Avanzados**: 
  - `ARRAY`, `JSON`, `JSONB`
  - `UUID`, `INET`, `CIDR`



<br/>
</details>

---

<details><summary><h3>Relaciones y Llaves</h3></summary>
<br/>

#### Llaves Primarias y Foráneas

Las llaves primarias y foráneas son esenciales para definir relaciones entre tablas y asegurar la integridad de los datos.

- **Llaves Primarias**: Un identificador único para cada fila de una tabla.
  ```sql
  CREATE TABLE usuarios (
    usuario_id SERIAL PRIMARY KEY,
    nombre VARCHAR(100)
  );
  ```
- **Llaves Foráneas**: Definen relaciones entre tablas y mantienen la integridad referencial.
  ```sql
  CREATE TABLE pedidos (
    pedido_id SERIAL PRIMARY KEY,
    usuario_id INT REFERENCES usuarios(usuario_id),
    fecha DATE
  );
  ```

#### Integridad Referencial

La integridad referencial asegura que las relaciones entre tablas sean consistentes y correctas.

- **Restricciones de Integridad Referencial**:
  - `ON DELETE CASCADE`
  - `ON UPDATE RESTRICT`



<br/>
</details>

---

<details><summary><h3>Índices y Vistas</h3></summary>
<br/>

#### Tipos de Índices y su Uso

Los índices mejoran la velocidad de acceso a los datos y son esenciales para optimizar el rendimiento de las consultas.

**Objetivo Específico:**
- Conocer los diferentes tipos de índices y su uso en PostgreSQL.

- **Índices Comunes**:
  - `B-tree` (por defecto y más común)
  - `Hash` (para igualdad)
  - `GIN` y `GiST` (para búsqueda de texto y espacial)
  ```sql
  CREATE INDEX idx_nombre ON usuarios(nombre);
  ```
- **Mantenimiento de Índices**:
  - Comando `REINDEX`
  - Uso de `VACUUM`

#### Creación y Uso de Vistas

Las vistas proporcionan una manera de simplificar consultas complejas y mejorar la seguridad al limitar el acceso a ciertos datos.

**Objetivo Específico:**
- Aprender a crear y utilizar vistas en PostgreSQL.

- **Creación de Vistas**:
  ```sql
  CREATE VIEW vista_usuarios AS
  SELECT nombre, edad FROM usuarios WHERE edad > 18;
  ```
- **Uso de Vistas**: Consultas más simples y control de acceso a datos específicos.

<br/>
</details>

---

<details><summary><h3>Prácticas</h3></summary>
<br/>

- [Cómo conectar pgAdmin y PostgreSQL desde Docker](pgadmindocker/README.md)

<br/>
</details>

---

### 💯 Conclusión

El diseño eficiente de bases de datos es fundamental para el rendimiento y la escalabilidad de cualquier aplicación. Esta sesión ha proporcionado una comprensión profunda del modelado de datos, la implementación de relaciones y llaves, y el uso de índices y vistas en PostgreSQL. Con estas habilidades, los administradores y desarrolladores estarán mejor equipados para diseñar y optimizar bases de datos, garantizando estructuras robustas y acceso eficiente a los datos.

### 🤓 Proyecto Modular

---

<details><summary><h3>Configuración del entorno SQL</h3></summary>
<br/>

Con el fin de que puedas poner todo tu conocimiento en práctica a lo largo de este módulo se realizarán distintas actividades que te permitirán ir construyendo un proyecto de manera progresiva y de manera guiada por los expertos. Este proyecto será el entregable final de todo del módulo y se dividirá en las siguientes etapas:

- [x] Creación de un repositorio   
- [x] Obtención de datos   
- [x] Configuración del entorno SQL   
- [ ] Diseño de la base de datos
- [ ] Gestión de usuarios
- [ ] Creando una copia de seguridad
- [ ] Optimizando consultas
- [ ] Preparando un proceso de réplica y alta disponibilidad
- [ ] Preparando el monitoreo
- [ ] Migración de datos
- [ ] Presentación del proyecto

---
 
#### :dart: Avance del Proyecto 4/10: Diseño de la base de datos

##### Actividad

- Diseñar el esquema de la base de datos.

⏰ Tiempo estimado: *60 minutos*

1. Definir las tablas necesarias y sus relaciones.

2. Especificar los tipos de datos y las restricciones.

3. Crear el esquema de la base de datos utilizando comandos SQL.

##### Resultado Esperado:

Un esquema de base de datos bien diseñado que incluya tablas, tipos de datos y relaciones.


</details>

---

[`< Regresar`](../README.md)
