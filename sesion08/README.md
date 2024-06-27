[`PostgreSQL Avanzado`](../README.md)

# Sesión 08: Alta Disponibilidad y Replicación

## 🌿 Introducción

La alta disponibilidad y la replicación son esenciales para asegurar que las bases de datos PostgreSQL estén siempre disponibles y puedan manejar grandes volúmenes de datos sin interrupciones. Esta sesión cubrirá las técnicas y herramientas necesarias para configurar y gestionar la replicación, los clústeres y el balanceo de carga, así como las soluciones de terceros que pueden mejorar estas capacidades.

## 🎯 Objetivos Generales

1. Comprender los conceptos y beneficios de la alta disponibilidad y la replicación en PostgreSQL.
1. Aprender a configurar y gestionar la replicación en PostgreSQL.
1. Implementar y gestionar clústeres y balanceo de carga para mejorar la disponibilidad y el rendimiento.
1. Conocer y utilizar soluciones de terceros para la alta disponibilidad y la replicación en PostgreSQL.

## 📚 Temario

1. **Replicación en PostgreSQL**

	- Objetivo: Configurar y gestionar la replicación en PostgreSQL.
	- Subtemas:
		- Introducción a la replicación
		- Configuración de la replicación en PostgreSQL
		- Tipos de replicación: síncrona y asíncrona
		- Monitoreo y mantenimiento de la replicación

2. **Clústeres y Balanceo de Carga**

	- Objetivo: Implementar clústeres y balanceo de carga para mejorar la disponibilidad y el rendimiento.
	- Subtemas:
		- Configuración de clústeres PostgreSQL
		- Implementación de balanceo de carga
		- Herramientas y técnicas para balanceo de carga
		- Ejemplos prácticos

3. **Soluciones de Terceros**

	- Objetivo: Conocer e implementar soluciones de terceros para mejorar la alta disponibilidad y la replicación.
	- Subtemas:
		- Visión general de las soluciones de terceros
		- Comparación de herramientas populares: Patroni, PgBouncer, etc.
		- Implementación y configuración de soluciones de terceros
		- Casos de uso y mejores prácticas

## 🚀 Desarrollo

---

<details><summary><h3>Replicación en PostgreSQL</h3></summary>
<br/>

#### Introducción a la Replicación

La replicación es el proceso de copiar datos de una base de datos a otra para garantizar la disponibilidad y la redundancia. PostgreSQL ofrece varias formas de replicación para satisfacer diferentes necesidades de rendimiento y disponibilidad.

#### Configuración de la Replicación

- **Configuración del Servidor Primario:**

	1. Editar el archivo `postgresql.conf` para habilitar la replicación:

		```ini	
		wal_level = replica
		max_wal_senders = 5
		wal_keep_size = 64MB
		```

	2. Editar el archivo `pg_hba.conf` para permitir conexiones de replicación:

		```ini
		host replication replicator 192.168.1.0/24 md5
		```

	3. Crear un usuario de replicación:

		```sql
		CREATE USER replicator WITH REPLICATION ENCRYPTED PASSWORD 'password';
		```

- **Configuración del Servidor Secundario:**

	1. Hacer una copia del servidor primario:

		```bash
		pg_basebackup -h primary_host -D /var/lib/postgresql/13/main -U replicator -v -P --wal-method=stream
		```

	2. Crear un archivo `recovery.conf`:

		```ini
		standby_mode = 'on'
		primary_conninfo = 'host=primary_host port=5432 user=replicator password=password'
		trigger_file = '/tmp/postgresql.trigger'
		```

	3. Iniciar el servidor secundario:

		```bash
		sudo systemctl start postgresql
		```

#### Tipos de Replicación: Síncrona y Asíncrona

- **Replicación Asíncrona:**

	- Los cambios se envían al servidor secundario después de ser confirmados en el servidor primario.
	- Menor impacto en el rendimiento del servidor primario.

- **Replicación Síncrona:**

	- Los cambios deben ser confirmados por al menos un servidor secundario antes de ser confirmados en el servidor primario.
	- Mayor consistencia a costa de un rendimiento ligeramente inferior.

#### Monitoreo y Mantenimiento de la Replicación

- Utilizar vistas del sistema como `pg_stat_replication` para monitorear el estado de la replicación:

	```sql
	SELECT * FROM pg_stat_replication;
	```

<br/>
</details>

---

<details><summary><h3>Clústeres y Balances Carga</h3></summary>
<br/>

#### Configuración de Clústeres PostgreSQL

La configuración de clústeres permite distribuir la carga de trabajo entre múltiples nodos para mejorar el rendimiento y la disponibilidad.

- **Herramientas Populares:** Patroni, Stolon.

- **Configuración Básica con Patroni:**

	1. Instalar Patroni:

		```bash
		pip install patroni[etcd]
		```

	2. Configurar Patroni en cada nodo:


		```yaml
		scope: postgresql-cluster
		namespace: /service/
		name: postgresql0

		etcd:
		  host: 127.0.0.1:2379

		bootstrap:
		  dcs:
		    ttl: 30
		    loop_wait: 10
		    retry_timeout: 10
		    maximum_lag_on_failover: 1048576

		    postgresql:
		      use_pg_rewind: true
		      parameters:
		        wal_level: replica
		        hot_standby: "on"
		        wal_keep_segments: 8
		        max_wal_senders: 5
		        max_replication_slots: 5
		        wal_log_hints: "on"
		```

	3. Iniciar Patroni:

		```bash
		patroni /path/to/patroni.yml
		```

#### Implementación de Balanceo de Carga

- **Utilizar PgBouncer para Balanceo de Carga:**

	1. Instalar PgBouncer:

		```bash
		sudo apt-get install pgbouncer
		```

	2. Configurar PgBouncer:

		```bash
		[databases]
		mydb = host=127.0.0.1 port=5432 dbname=mydb

		[pgbouncer]
		listen_addr = 0.0.0.0
		listen_port = 6432
		auth_type = md5
		auth_file = /etc/pgbouncer/userlist.txt
		```

	3. Iniciar PgBouncer:

		```bash
		pgbouncer /etc/pgbouncer/pgbouncer.ini
		```

#### Herramientas y técnicas para Balanceo de Carga

- **HAProxy**: Utilizado para distribuir la carga de trabajo entre múltiples servidores PostgreSQL.

	- Configuración básica:

		```ini
		frontend pgsql_front
		    bind *:5000
		    mode tcp
		    default_backend pgsql_back

		backend pgsql_back
		    mode tcp
		    balance roundrobin
		    server pgsql1 192.168.1.10:5432 check
		    server pgsql2 192.168.1.11:5432 check
		```


<br/>
</details>

---

<details><summary><h3>Soluciones de Terceros</h3></summary>
<br/>

#### Visión General de las Soluciones de Terceros

Existen varias soluciones de terceros que pueden mejorar la alta disponibilidad y la replicación en PostgreSQL.

#### Comparación de Herramientas Populares

- **Patroni:** Automatiza el proceso de failover y replicación, integrándose bien con herramientas como etcd y Consul.

- **PgBouncer:** Un pool de conexiones ligero para PostgreSQL, ideal para balanceo de carga y manejo de muchas conexiones concurrentes.

- **Stolon:** Una solución nativa de la nube para alta disponibilidad de PostgreSQL, diseñada para ser resiliente y flexible.

#### Implementación y Configuración de Soluciones de Terceros

- **Implementación de Patroni:**

	- Ya abordado en la sección de configuración de clústeres y balanceo de carga.

- **Configuración de PgBouncer:**

	- Ya abordado en la sección de balanceo de carga.

#### Casos de Uso y Mejores Prácticas

- **Patroni:** Ideal para entornos que requieren failover automático y una configuración sencilla.

- **PgBouncer:** Perfecto para aplicaciones que manejan muchas conexiones cortas y necesitan un pool de conexiones eficiente.

- **Stolon:** Adecuado para entornos de nube donde la flexibilidad y la resiliencia son cruciales.


<br/>
</details>

---

### 💯 Conclusión

La alta disponibilidad y la replicación son componentes esenciales para garantizar que las bases de datos PostgreSQL estén siempre disponibles y funcionen de manera eficiente. Este curso ha cubierto la configuración y gestión de la replicación, los clústeres y el balanceo de carga, así como las soluciones de terceros que pueden mejorar estas capacidades. Con este conocimiento, los administradores de bases de datos pueden asegurar que sus sistemas sean robustos, escalables y capaces de manejar las demandas de las aplicaciones modernas.

[`Anterior`](../sesion07/tema04/README.md) | [`Siguiente`](tema01/README.md)