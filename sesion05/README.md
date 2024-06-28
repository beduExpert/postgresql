[`PostgreSQL Avanzado`](../README.md)

# Sesión 05: Gestión de Usuarios, Seguridad y Privilegios en PostgreSQL

## 🌿 Introducción

En cualquier sistema de gestión de bases de datos, la gestión de usuarios, la seguridad y los privilegios son fundamentales para proteger la integridad y la confidencialidad de los datos. Esta sesión está diseñada para proporcionar un conocimiento profundo y práctico sobre cómo gestionar usuarios y roles, asegurar PostgreSQL y aplicar políticas de seguridad y auditoría.

## 🎯 Objetivos Generales

1. Comprender cómo crear y gestionar usuarios y roles en PostgreSQL.
2. Aprender técnicas avanzadas de seguridad para proteger datos y conexiones.
3. Implementar políticas de seguridad y auditoría para monitorear y controlar el acceso a la base de datos.

## 📚 Temario

### Temario

1. **Gestión de Usuarios y Roles:**
   - Creación de usuarios y roles.
   - Asignación de privilegios.

2. **Seguridad en PostgreSQL:**
   - Autenticación y autorización.
   - Cifrado y seguridad en la red.

3. **Políticas de Seguridad y Auditoría:**
   - Implementación de políticas de acceso.
   - Monitoreo y auditoría de actividades.

## 🚀 Desarrollo

---

<details><summary><h3>Gestión de Usuarios y Roles</h3></summary>
<br/>

#### Creación de usuarios y roles
En PostgreSQL, los usuarios y roles se utilizan para gestionar el acceso y las tareas de los diferentes usuarios de la base de datos.

- **Pasos para la creación de usuarios y roles:**
  1. Crear un usuario.
  2. Crear un rol.
  3. Asignar un rol a un usuario.

- **Ejemplo:**
  ```sql
  CREATE USER usuario1 WITH PASSWORD 'password123';
  CREATE ROLE rol_lectura;
  GRANT rol_lectura TO usuario1;
  ```

#### Asignación de privilegios
Los privilegios determinan qué operaciones puede realizar un usuario o rol en una base de datos.

- **Pasos para asignar privilegios:**
  1. Asignar privilegios a nivel de base de datos.
  2. Asignar privilegios a nivel de tabla.
  3. Revocar privilegios.

- **Ejemplo:**
  ```sql
  GRANT SELECT ON ALL TABLES IN SCHEMA public TO rol_lectura;
  REVOKE SELECT ON ALL TABLES IN SCHEMA public FROM rol_lectura;
  ```

<br/>
</details>

---

<details><summary><h3>Seguridad en PostgreSQL</h3></summary>
<br/>

#### Autenticación y autorización
La autenticación verifica la identidad de los usuarios que intentan acceder a PostgreSQL, mientras que la autorización determina los permisos de los usuarios autenticados.

- **Métodos de autenticación:**
  1. Password.
  2. MD5.
  3. SCRAM-SHA-256.
  4. LDAP.
  5. Certificados SSL.

- **Ejemplo:**
  ```sh
  # Modificar pg_hba.conf
  host all all 0.0.0.0/0 md5
  ```

#### Cifrado y seguridad en la red
El cifrado asegura que los datos transmitidos entre el cliente y el servidor no puedan ser leídos por terceros.

- **Pasos para habilitar SSL:**
  1. Generar certificados.
  2. Configurar PostgreSQL para usar SSL.
  3. Verificar la conexión segura.

- **Ejemplo:**
  ```sh
  # Generar certificados SSL
  openssl req -new -text -out server.req
  openssl rsa -in privkey.pem -out server.key
  openssl req -x509 -in server.req -text -key server.key -out server.crt

  # Configurar postgresql.conf
  ssl = on
  ssl_cert_file = 'server.crt'
  ssl_key_file = 'server.key'
  ```


<br/>
</details>

---

<details><summary><h3>Políticas de Seguridad y Auditoría</h3></summary>
<br/>

#### Implementación de políticas de acceso
Las políticas de acceso ayudan a definir y controlar los permisos sobre los datos.

- **Pasos para implementar políticas de acceso:**
  1. Crear políticas de fila.
  2. Asignar políticas a tablas.

- **Ejemplo:**
  ```sql
  CREATE POLICY politica_lectura
  ON tabla1
  FOR SELECT
  USING (true);

  ALTER TABLE tabla1 ENABLE ROW LEVEL SECURITY;
  ```

##### Monitoreo y auditoría de actividades
El monitoreo y la auditoría permiten rastrear las acciones realizadas en la base de datos para detectar y prevenir actividades no autorizadas.

- **Herramientas de auditoría:**
  1. pgAudit.
  2. Log de PostgreSQL.
  3. Herramientas de terceros.

- **Ejemplo:**
  ```sh
  # Configurar postgresql.conf para auditoría
  shared_preload_libraries = 'pgaudit'
  pgaudit.log = 'all'
  ```


<br/>
</details>

---

### 💯 Conclusión

La gestión de usuarios, la seguridad y los privilegios son componentes esenciales para mantener la integridad y la confidencialidad de los datos en PostgreSQL. A través de este módulo, los participantes adquirirán las habilidades necesarias para gestionar usuarios y roles, implementar medidas de seguridad avanzadas y establecer políticas de seguridad y auditoría efectivas.

### 🤓 Proyecto Modular

---

<details><summary><h3>Gestión de Usuarios</h3></summary>
<br/>

Con el fin de que puedas poner todo tu conocimiento en práctica a lo largo de este módulo se realizarán distintas actividades que te permitirán ir construyendo un proyecto de manera progresiva y de manera guiada por los expertos. Este proyecto será el entregable final de todo del módulo y se dividirá en las siguientes etapas:

- [x] Creación de un repositorio   
- [x] Obtención de datos   
- [x] Configuración del entorno SQL   
- [x] Diseño de la base de datos
- [ ] Gestión de usuarios
- [ ] Creando una copia de seguridad
- [ ] Optimizando consultas
- [ ] Preparando un proceso de réplica y alta disponibilidad
- [ ] Preparando el monitoreo
- [ ] Migración de datos
- [ ] Presentación del proyecto

---
 
#### :dart: Avance del Proyecto 5/10: Gestión de usuarios

##### Actividad

⏰ Tiempo estimado: *60 minutos*

1. **Crear usuarios y roles**:

  - Define los usuarios y roles necesarios para el proyecto.
  - Asigna privilegios adecuados a cada usuario y rol.

2. **Escribir el script de creación de usuarios y roles**:

  - Guarda el script en la carpeta `scripts`.

**Ejemplo**:

```
CREATE USER analista WITH PASSWORD 'password123';
CREATE ROLE readonly;

GRANT CONNECT ON DATABASE proyecto_db TO readonly;
GRANT USAGE ON SCHEMA public TO readonly;
GRANT SELECT ON ALL TABLES IN SCHEMA public TO readonly;

GRANT readonly TO analista;
```

</details>

---

[`< Regresar`](../README.md)
