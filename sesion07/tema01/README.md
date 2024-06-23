[`PostgreSQL Avanzado`](../../README.md) > [`Sesión 07`](../README.md)

<img src="../imagenes/img01.jpg" width="45%" align="right" hspace=30>

### 7.1. Optimización de Consultas

#### 🎯 Objetivos

- Comprender cómo interpretar y utilizar el plan de ejecución de consultas.

- Aprender a utilizar índices para mejorar la velocidad de recuperación de datos.

- Implementar estrategias para optimizar consultas en **PostgreSQL**

---

#### 🌱 Desarrollo

<details><summary><b><u>Plan de Ejecución de Consultas</u></b></summary>
<br/>

El plan de ejecución de una consulta es una representación detallada de cómo **PostgreSQL** ejecutará una consulta SQL. Comprender este plan es esencial para identificar cuellos de botella y optimizar el rendimiento.

**Visualización del Plan de Ejecución**

- Utilizar `EXPLAIN` para obtener el plan de ejecución de una consulta.

- Utilizar `EXPLAIN ANALYZE` para obtener estadísticas de tiempo real sobre la ejecución de la consulta.

<br>

```sql
EXPLAIN SELECT * FROM users WHERE age > 30;
EXPLAIN ANALYZE SELECT * FROM users WHERE age > 30;
```

**Interpretación del Plan**

- **Seq Scan**: Escaneo secuencial de una tabla

- **Index Scan**: Escaneo utilizando un índice

- **Nexted Loop, Hash Join, Merge Join**: Diferentes métodos de combinación de tablas.

<br/>
</details>

<details><summary><b><u>Uso de Índices y Optimización de Consultas</u></b></summary>
<br/>

Los índices son estructuras de datos que mejorar la velocidad de recuperación de datos en las tablas a costa de un mayor uso de espacio y tiempo adicional para las operaciones de escritura.

**Tipos de índices**

- **B-tree**: Índice predeterminado, bueno para igualdad y rangos.

- **Hash**: Optimizado para igualdad.

- **GIN y GiST**: Para búsquedad de texto completo y datos geoespaciales.

```sql
CREATE INDEX idx_user_age ON user(age);
```

**Estrategias de Optimización**

- **Selección de Índices**: Crear índices en columnas que se usan frecuentemente en clásulas `WHERE` y `JOIN`.

- **Índices Compuestos**: Útiles para consultas que filtran por más de una columna.

	```sql
	CREATE INDEX idx_users_age_city ON users(age,city);
	```

- **Índices Parciales**: Crear índices sólo para subconjuntos específicos de datos.

	```sql
	CREATE INDEX idx_users_active ON users(agre) WHERE active = true;
	```

<br/>
</details>

---

#### 🧐 Actividades

- [`Ejemplo 1`](ejemplo01/README.md)

---

[`Anterior`](../README.md) | [`Siguiente`](ejemplo01/README.md)
