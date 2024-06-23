[`PostgreSQL Avanzado`](../../../README.md) > [`Sesión 07`](../../README.md) > [`Manejo de Transacciones en PostgreSQL`](../README.md)

### Ejemplo 2

#### 1️⃣ Introducción

En este ejemplo, aprenderás a manejar transacciones en PostgreSQL usando los conceptos ACID, bloqueo, y concurrencia. Utilizaremos pgAdmin 4 para ejecutar los comandos y observar los resultados.

---

#### 2️⃣ Objetivos

1. Comprender y aplicar las propiedades ACID en transacciones.

2. Manejar transacciones usando los comandos `BEGIN`, `COMMIT` y `ROLLBACK`.

3. Identificar y gestionar bloqueos y problemas de concurrencia en PostgreSQL.

---

#### 3️⃣ Prerrequisitos

- Tener **PostgreSQL** y **pgAdmin 4** instalados.

- Usaremos la base de datos "dvdreltal" nuevamente.

---

#### 4️⃣ Comprender las Propiedades ACID

**Propiedades ACID**

- **Atomicidad**: Las transacciones son todo o nada.

- **Consistencia**: Las transacciones llevan al sistema de un estado válido a otro estado válido.

- **Aislamiento**: Las transacciones concurrentes se ejecutan como si fueran secuenciales.

- **Durabilidad**: Una vez que una transacción ha sido confirmada, los cambios son permanentes.

--- 

#### 5️⃣ Manejo Básico de Transacciones.

**Uso de `BEGIN`, `COMMIT` y `ROLLBACK`**

1. Abre pgAdmin 4 y conéctate a tu servidor PostgreSQL.

2. Selecciona la base de datos "dvdrental".

3. Abre la herramienta de consulta (Query Tool).

4. **Iniciar una Transacción**:

   ```sql
   BEGIN
   ```

5. **Ejecutar Operaciones dentro de la Transacción**:

   ```sql
   INSERT INTO category (name) VALUES ('New Category');
   ```

6. **Confirmar la Transacción**:

   ```sql
   COMMIT;
   ```

7. **Ejemplo de Rollback:**

   - Iniciar una nueva transacción:

      ```sql
      BEGIN;
      ```

   - Insertar una nueva categoría:

      ```sql
      INSERT INTO category (name) VALUES ('Temporary Category');
      ```

   - Revertir los cambios:

      ```sql
      ROLLBACK;
      ```

8. **Verificar los Cambios**:

   ```sql
   SELECT * FROM category WHERE name IN ('New Category', 'Temporary Category');
   ```

   Sólo deberías ver "New Category" en los resultados.   

---

#### 6️⃣ Bloqueos y Concurrencia

**Identificación de Bloqueos**

Un bloqueo es un mecanismo que controla el acceso concurrente a los datos de una base de datos para asegurar la integridad y consistencia de la información. Los bloqueos garantizan que las transacciones concurrentes no interfieran entre sí de manera perjudicial.

Son esenciales para gestionar el acceso concurrente a los datos, asegurando la integridad y consistencia de la base de datos en entornos multiusuario.

Bloqueo de filas (Row Locks)

| Tipo | Descripción |
| :--: | :---------- |
| **Exclusive Lock** | Una transacción que ha obtenido un bloqueo exclusivo sobre una fila impide que otras transacciones la modifiquen hasta que el bloqueo se libere. |
| **Share Lock** | Permite que múltiples transacciones lean una fila al mismo tiempo, pero impide que la fila sea modificada mientras el bloqueo compartido esté en vigor. |

Bloqueo de tablas (Table Locks)

| Tipo | Descripción |
| :--: | :---------- |
| **ACCESS SHARE** | Permite que una transacción lea una tabla mientras otras transacciones también pueden leerla. |
| **Share Lock** | Impide que otras transacciones lean o modifiquen la tabla hasta que se libere el bloqueo. |

1. **Ver Bloqueos Actuales:**

   ```sql
   SELECT * FROM pg_locks;
   ```

2. **Ejemplo de Bloqueo con pgAdmin**:

   - **Sesión 1**: Abre una nueva sesión de consulta y ejecuta:

      ```sql
      BEGIN;
      UPDATE film SET rental_rate = 5.99 WHERE film_id = 1;
      ```

   - **Sesión 2**: Abre otra sesión de consulta y ejecuta:

      ```sql
      BEGIN;
      UPDATE film SET rental_rate = 4.99 WHERE film_id = 1;
      ```

      La segunda sesión se bloqueará hasta que la primera sesión confirme o revierta la transacción.

   - **Sesión 1**: Ejecuta `COMMIT` o `ROLLBACK` para liberar el bloqueo.

**Niveles de Aislamiento**

El nivel de aislamiento es una configuración en sistema de bases de datos que determina cómo se manejan las transacciones concurrentes para garantizar la integridad y consistencia de los datos. Define el grado en que una transacción debe ser aislada de otras transacciones concurrentes, afectando la visibilidad de los cambios no confirmados entre ellas.

Niveles de Aislamiento:

- **Read Uncommitted (Lectura No Confirmada)**:

   - Permite leer datos no confirmados por otras transacciones.
   - Mayor riesgo de inconsistencias (lecturas sucias).

- **Read Committed (Lectura Confirmada)**:

   - Solo permite leer datos confirmados por otras transacciones.
   - Previene lecturas sucias, pero no evita lecturas no repetibles ni lecturas fantasma.
   - Es el nivel de aislamiento predeterminado en PostgreSQL.

- **Repeatable Read (Lectura Repetible)**:

   - Garantiza que si una transacción lee una fila, cualquier lectura posterior de la misma fila en la misma transacción verá los mismos datos, incluso si otras transacciones las modifican.
   - Evita lecturas no repetibles, pero no lecturas fantasma.

- **Serializable**:

   - Proporciona el nivel de aislamiento más alto, garantizando que las transacciones se ejecuten de manera que el resultado sea el mismo que si se hubieran ejecutado secuencialmente.
   - Evita lecturas sucias, lecturas no repetibles y lecturas fantasma.
   - Puede reducir la concurrencia y aumentar los bloqueos.


1. **Ver Nivel de Aislamiento Actual**:

   ```sql
   SHOW default_transaction_isolation;
   ```

2. **Configurar Nivel de Aislamiento**:

   ```sql
   SET TRANSACTION ISOLATION LEVEL SERIALIZABLE;
   ```

3. **Ejemplo de Nivel de Aislamiento**:

   - **SERIALIZABLE**:

      ```sql
      SET TRANSACTION ISOLATION LEVEL SERIALIZABLE;
      BEGIN;
      SELECT * FROM film WHERE rating = 'PG';
      -- Ejecuta alguna modificación en otra sesión y luego intenta realizar una operación en esta sesión para ver el efecto del nivel de aislamiento.
      COMMIT;
      ```
---

#### 7️⃣ Manejo de Concurrencia

**Ejemplo de Problema de Concurrencia**

1. **Phantom Reads**:

   Un "phantom read" (lectura fantasma) es un fenómeno en bases de datos relacionales que ocurre cuando una transacción ejecuta una consulta que devuelve un conjunto de filas que satisfacen cierta condición, pero otra transacción inserta nuevas filas que también cumplen con esa condición antes de que la primera transacción haya finalizado.

   - **Sesión 1**:

      ```sql
      SET TRANSACTION ISOLATION LEVEL READ COMMITTED;
      BEGIN;
      SELECT COUNT(*) FROM film WHERE rating = 'PG';
      -- Mantén la transacción abierta
      ```

   - **Sesión 2**:

      ```sql
      BEGIN;
      INSERT INTO film (title, description, release_year, language_id, rental_duration, rental_rate, length, replacement_cost, rating, last_update) 
      VALUES ('New Movie', 'Description', 2023, 1, 3, 4.99, 120, 20.99, 'PG', NOW());
      COMMIT;
      ```

   - **Sesión 1**:

      ```sql
      SELECT COUNT(*) FROM film WHERE rating = 'PG';
      COMMIT;
      ```

      Observa como la segunda consulta en la sesión 1 incluye la nueva fila, demostrando un phantom read.

---

#### 8️⃣ Conclusión

A través de este ejemplo, has aprendido a manejar transacciones en PostgreSQL, aplicar las propiedades ACID, gestionar bloqueos y niveles de aislamiento, y entender problemas de concurrencia. Estas habilidades son esenciales para garantizar la integridad y consistencia de los datos en aplicaciones de base de datos concurrentes. Practica regularmente para familiarizarte con estos conceptos y mejorar tu capacidad de manejar transacciones de manera eficiente.


[`Anterior`](../README.md) | [`Siguiente`](../../tema03/README.md)
