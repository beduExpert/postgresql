[`PostgreSQL Avanzado`](../../../README.md) > [`Sesión 06`](../../README.md) > [`Estrategias de Recuperación`](../README.md)

#### Ejemplo 3: Configurar WAL


Configurar WAL (Write-Ahead Logging) en PostgreSQL es esencial para implementar estrategias de recuperación de datos, como Point-In-Time Recovery (PITR). Aquí hay un resumen de todos los comandos en un flujo de trabajo completo:

```sh
# Paso 1: Editar el archivo de configuración
sudo nano /var/lib/postgresql/12/main/postgresql.conf

# Añadir las siguientes líneas en postgresql.conf:
# wal_level = replica
# archive_mode = on
# archive_command = 'cp %p /var/lib/postgresql/12/wal_archive/%f'
# checkpoint_timeout = 5min
# max_wal_size = 1GB
# min_wal_size = 80MB

# Paso 2: Crear el directorio de archivo
sudo mkdir -p /var/lib/postgresql/12/wal_archive
sudo chown postgres:postgres /var/lib/postgresql/12/wal_archive
sudo chmod 700 /var/lib/postgresql/12/wal_archive

# Paso 3: Reiniciar PostgreSQL
sudo systemctl restart postgresql

# Verificación
psql -U postgres -d postgres -c "SHOW wal_level;"
psql -U postgres -d postgres -c "SHOW archive_mode;"
psql -U postgres -d postgres -c "SHOW archive_command;"
```

##### Configuración adicional para el PITR

Para realizar una recuperación a un punto en el tiempo (PITR), se deben seguir estos pasos adicionales:

1. Realizar una copia de seguridad base:

```sh
pg_basebackup -D /ruta/a/backup -Fp -Xs -P -U postgres
```

2. Guardar los archivos WAL generados después de la copia de seguridad base en el directorio de archivo especificado.

3. Para recuperar la base de datos a un punto en el tiempo específico:

    - Detén PostgreSQL:

    ```sh
    sudo systemctl stop postgresql
    ```

    - Borra el contenido del directorio de datos o muévelo a una ubicación segura:

    ```sh
    mv /var/lib/postgresql/12/main /var/lib/postgresql/12/main_old
    ```

    - Restaura la copia de seguridad base:

    ```sh
    cp -R /ruta/a/backup /var/lib/postgresql/12/main
    ```

    - Crea un archivo de recuperación (`recovery.conf`) en el directorio de datos:

    ```sh
    echo "restore_command = 'cp /var/lib/postgresql/12/wal_archive/%f %p'" > /var/lib/postgresql/12/main/recovery.conf
    echo "recovery_target_time = '2024-06-23 12:00:00'" >> /var/lib/postgresql/12/main/recovery.conf
    ```

    - Asegúrate de que los permisos y propietarios sean correctos:

    ```sh
    chown -R postgres:postgres /var/lib/postgresql/12/main
    chmod -R 700 /var/lib/postgresql/12/main
    ```

    - Inicia PostgreSQL:

    ```sh
    sudo systemctl start postgresql
    ```

Con estos pasos, puedes configurar correctamente WAL en PostgreSQL, incluyendo la posibilidad de realizar un Point-In-Time Recovery (PITR).

[`Anterior`](../../tema04/README.md) | [`Siguiente`](../../tema05/README.md)
