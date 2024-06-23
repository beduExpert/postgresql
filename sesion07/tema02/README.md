[`PostgreSQL Avanzado`](../../README.md) > [`Sesión 07`](../README.md)

<img src="../imagenes/img01.jpg" width="45%" align="right" hspace=30>

### 7.2. Manejo de Transacciones

#### 🎯 Objetivos

- Entender los principios ACID y su aplicación en PostgreSQL.

- Aprender a manejar transacciones de manera eficiente para garantizar la integridad de los datos.

- Comprender los mecanismos de bloqueo y concurrencia para optimizar el acceso concurrente a la base de datos.

---

#### 🌱 Desarrollo

<details><summary><b><u>ACID y Manejo de Transacciones</u></b></summary>
<br/>

ACID es un conjunto de propiedades que garantizan la fiabilidad de las transacciones en las bases de datos.

- **Atomicidad**: Todas las operaciones dentro de una transacción se completan o ninguna se completa.

- **Consistencia**: Una transacción lleva la base de datos de un estado válido a otro válido.

- **Aislamiento**: Las transacciones concurrentes se ejecutan como si fueran secuenciales.

- **Durabilidad**: Una vez que una transacción se completa, sus cambios son permanentes.

```sql
BEGIN;
UPDATE accounts SET balance = balance - 100 WHERE user_id = 1;
UPDATE accounts SET balance = balance + 100 WHERE user_id = 2;
COMMIT;
```

<br/>
</details>

<details><summary><b><u>Bloqueo y Concurrencia</u></b></summary>
<br/>

PostgreSQL maneja el acceso concurrente a los datos mediante un sistema de bloqueo.

**Tipos de Bloqueo**

- **Row-level locks**: Bloqueo de filas individuales.

- **Table-level locks**: Bloqueo de tablas enteras.

```sql
SELECT * FROM accounts WHERE user_id = 1 FOR UPDATE;
```

**Niveles de Aisamiento** 

- **Read Committed**: Las transacciones sólo ven cambios confirmados.

- **Repeatable Read**: Las transacciones ven un estado consistente de la base de datos al comienzo de la transacción.

- **Serializable:** Las transacciones se ejecutan como si fueran secuenciales.

```sql
SET TRANSACTION ISOLATION LEVEL REPEATABLE READ;
```

<br/>
</details>

---

#### 🧐 Actividades

- [`Ejemplo 2`](ejemplo02/README.md)

---

[`Anterior`](../tema01/ejemplo01/README.md) | [`Siguiente`](ejemplo02/README.md)
