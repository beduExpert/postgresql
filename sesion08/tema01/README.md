[`PostgreSQL Avanzado`](../../README.md) > [`Sesión 07`](../README.md)

<img src="../imagenes/img01.jpg" width="45%" align="right" hspace=30>

### 8.1. Optimización de Consultas

#### 🎯 Introducción

La replicación es el proceso de copiar datos de una base de datos a otra para garantizar la disponibilidad y la redundancia. PostgreSQL ofrece varias formas de replicación para satisfacer diferentes necesidades de rendimiento y disponibilidad.

---

#### 🌱 Desarrollo

<details><summary><b><u>Configuración del Servidor Primario</u></b></summary>
<br/>

**Configuración del Servidor Primario**

- Editar el archivo `postgresql.conf`:

	```Ini
	wal_level = replica
	max_wal_senders = 3
	wal_keep_segments = 64
	```

- Editar el archivo `pg_hba.conf` para permitir conexiones de replicación:

	```Ini
	host replication
	replicator 192.168.1.0/24
	md5
	```

- Reiniciar el servidor de PostgreSQL.

**Configuración del Servidor Secundario**

- Hacer una copia del servidor primario.

	```Bash
	pg_basebackup -h primary_host -D /var/lib/postgresql/12/main -U replicator -v -P --wal-method=stream
	```

- Crear un archivo.

	```Ini
	standby_mode = 'on'
	primary_conninfo = 'host=primary_host port=5432 user=replicator password=your_password'
	trigger_file = '/tmp/postgresql.trigger'
	```

- Iniciar el servidor secundario.

<br/>
</details>

<details><summary><b><u>Tipos de Replicación: Síncrona y Asíncrona</u></b></summary>
<br/>

**Replicación Asíncrona**

- Los cambios se envían al servidor secundario después de ser confirmados en el servidor primario.

- Menor impacto en el rendimiento del servidor primario.

**Replicación Síncrona**

- Los cambios deben ser confirmados por al menos un servidor secundario antes de ser confirmados en el servidor primario.

- Mayor consistencia a costa de un rendimiento ligeramente inferior.

<br/>
</details>

<details><summary><b><u>Monitoreo y Mantenimiento de la Replicación</u></b></summary>
<br/>

Utilizar vistas del sistema como `pg_stat_replication` para monitorear el estado de la replicación:

```sql
SELECT *
FROM pg_stat_replication;
```

<br/>
</details>

---

#### 🧐 Actividades

- [`Ejemplo 1`](ejemplo01/README.md)

---

[`Anterior`](../README.md) | [`Siguiente`](ejemplo01/README.md)
