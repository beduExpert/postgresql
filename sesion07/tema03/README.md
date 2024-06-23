[`PostgreSQL Avanzado`](../../README.md) > [`Sesión 07`](../README.md)

<img src="../imagenes/img01.jpg" width="45%" align="right" hspace=30>

### 7.3. Ajustes de Configuración para Rendimiento

#### 🎯 Objetivos

- Identificar y configurar los parámetros de PostgreSQL que impactan en el rendimiento.

- Aprender técnicas de ajuste del servidor para mejorar la eficiencia de PostgreSQL.

- Aplicar ajustes específicos para optimizar el rendimiento de consultas y operaciones.

---

#### 🌱 Desarrollo

<details><summary><b><u>Parámetros de Configuración Importantes</u></b></summary>
<br/>

PostrgreSQL permite ajustar numerosos parámetros para optimizar el rendimiento del servidor.

- **shared_buffers**: Define la cantidad de memoria disponible para el almacenamiento en caché de datos.

- **work_mem**: Define la cantidad de memoria disponible para operaciones de ordenació y hash.

- **maintenance_work_mem**: Memoria utilizada para tareas de mantenimiento como la creación de índices.

- **effective_cache_size**: Indica al optimizador cuánta memoria del sistema operativo está disponible para la caché.

```conf
shared_buffers = 4GB
work_mem = 64MB
maintenance_work_mem = 1GB
effective_cache_size = 12GB
```

<br/>
</details>

<details><summary><b><u>Técnicas de Tuning del Servidor</u></b></summary>
<br/>

Ajustar el servidor de PostgreSQL implica identificar y modificar parámetros específicos para mejorar el rendimiento.

- **Autovacuum**: Asegurar que el proceso autovacuum esté configurado correctamente para evitar el bloat (crecimiento excesivo y no deseado del tamaño físico de una tabla y sus índices, debido a la acumulación de espacio muerto) de tablas. 

	```conf
	autovacuum = on
	autovacuum_max_workers = 3
	autovacuum_naptime = 60
	autovacuum_vacuum_cost_delay = 20ms
	```

- **Parámetros de Checkpoint**: Ajustar la frecuencia y el tamaño de los checkpoints para equilibrar la escritura de datos y la recuperación en caso de falla.

	```conf
	checkpoint_timeout = 15min
	max_wal_size = 2GB
	min_wal_size = 80MB
	```

- **Configuración de la Red**: Ajustar parámetros como `max_connections`, `listen_addresses` y `efective_io_concurrency`.

	```conf
	max_connections = 100
	listen_addresses = '*'
	effective_io_concurrency = 2
	```

<br/>
</details>

---

#### 🧐 Actividades

- [`Ejemplo 3`](ejemplo03/README.md)

---

[`Anterior`](../tema02/ejemplo02/README.md) | [`Siguiente`](ejemplo03/README.md)
