<style>
    *{
        margin: 0.5rem 0 0;
    }
</style>

# Jmix Superset

## Índice
1. [Introducción](Superset.md#Introducción)
2. [Configuración](Superset_config.md#Configuración)
3. [Dataset](Superset_dataset.md#Dataset)
4. [Gráficos](Superset_graficos.md#Gráficos)
5. [Dashboard](Superset_dashboard.md#Dashboard)

## Dataset

En esta sección, aprenderás a crear una conexión a la base de datos y un dataset en Apache Superset

### Crear una conexión a la base de datos

Cuando Superset está en ejecución, puedes crear una conexión a la base de datos que contiene los datos para los dashboards. En los pasos anteriores, al configurar los contenedores de Superset en el archivo `docker-compose-non-dev.yml`, creaste el servicio `jmix_database`, que inicia una instancia de PostgreSQL. Esta base de datos se utiliza en la aplicación Jmix, y ahora configurarás una conexión a esta base de datos en Superset.

En Superset, haz clic en el elemento **Database Connections** en la configuración.

<img src="https://docs.jmix.io/jmix/superset/_images/settings-databsase-connections.png" alt="Configuración Superset Database 1">

Crea una nueva conexión de base de datos. Selecciona el tipo `PostgreSQL` e ingresa los detalles de la conexión:

- **Host**: `jmix_database`
- **Puerto:** `5432` (o el puerto configurado en Docker).
- **Nombre de la Base de Datos:** `onboarding` (o el nombre de la base de datos que estás utilizando).
- **Usuario y Contraseña:** Las credenciales configurados para PostgreSQL (en este caso `jmix/jmix`).

<img src="https://docs.jmix.io/jmix/superset/_images/new-database-connection.png" width="20%" alt="Configuración Superset Database 2">

Haz clic en el botón **CONNECT** y luego en **FINISH**. Se ha creado la conexión al servicio `jmix_database`.

### Crear un Dataset

En Apache Superset, un **dataset** es una colección de datos que se puede utilizar para crear gráficos. Puede ser un dataset físico (una tabla o vista en una base de datos) o un dataset virtual (una consulta guardada que se reutiliza como dataset).

En este caso, utilizaremos una consulta SQL para crear un dataset virtual que combine datos de las tablas `USER_` y `DEPARTMENT` de la base de datos `Onboarding`.

En el menú superior, dirígete a **SQL**, selecciona **SQL Lab** y completa los siguientes campos:

- **DATABASE:** `Jmix Onboarding`.
- **SCHEMA:** `public`.

Ahora escribiremos la consulta que vamos a utilizar como dataset. Para ver los salarios de los empleados incluyendo el departamento de cada uno, escribe la siguiente consulta SQL:

```sql
SELECT CONCAT(first_name, ' ', last_name) AS full_name, 
    dpr.name AS department_name, 
    usr.salary
FROM public.user_ usr
INNER JOIN department dpr ON usr.department_id = dpr.id;
```

Esta consulta combina las tablas `USER_` y `DEPARTMENT` utilizando un `INNER JOIN` para evitar usuarios sin departamento (como el usuario administrador).

Ejecuta la consulta para verificar los resultados. Deberías ver una lista de empleados con su nombre completo, departamento y salario.

<img src="https://docs.jmix.io/jmix/superset/_images/sql-lab.png" width="50%" alt="Resultado de SQL Lab">

Guarda la consulta con el nombre **Employees' salaries** (Salarios de Empleados).