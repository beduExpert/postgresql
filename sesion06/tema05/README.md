[`PostgreSQL Avanzado`](../../README.md) > [`Sesión 06`](../README.md)

### 6.5. Conclusiones

![img](../imagenes/img19.jpg)

#### Comparación

| Característica | Copia de seguridad lógica | Copia de seguridad física |
| :--- | :--- | :--- |
| Herramientas | `pg_dump`, `pg_dumpall`, PgAdming 4 | `pg_basebackup`, `rsync`, `tar` |
| Formato | SQL, binario (tar, custom) | Archivos del sistema de datos |
| Independencia | Independiente del hardware | Dependiente del hardware |
| Velocidad de restauración | Más lenta para grandes bases de datos | Más rápida |
| Flexibilidad | Alta (selección de objetos, migración entre versiones) | Baja (generalmente misma versión) |
| Complejidad | Menor, más fácil de manejar | Mayor, requiere de WAL | 

#### Conclusión

- **Copia de Seguridad Lógica:** Ideal para exportaciones individuales de bases de datos, migraciones y restauraciones selectivas. Es más flexible y portátil.
- **Copia de Seguridad Física:** Ideal para la recuperación rápida de todo el clúster de bases de datos y para configuraciones de alta disponibilidad como replicación. Es más rápida y completa pero menos flexible.

Elegir el método adecuado dependerá de las necesidades específicas de tu entorno y de los requisitos de recuperación y portabilidad de tus datos.

<br/>

[`Anterior`](../tema04/ejemplo03/README.md) | [`Siguiente`](../../sesion07/README.md)
