# Jmix Superset

## Índice
1. [Introducción](Superset.md#Introducción)
2. [Configuración](Superset_config.md#Configuración)
3. [Dataset](Superset_dataset.md#Dataset)
4. [Gráficos](Superset_graficos.md#Gráficos)
5. [Dashboard](Superset_dashboard.md#Dashboard)

## Gráficos

En Apache Superset, los gráficos son una representación visual de los datos provenientes de un dataset. Puede ser de varios tipos, como Gráfico de barras, Gráfico circular, Tablas, etc.

Los gráficos se pueden combinar en dashboards.

En este caso veremos tres gráficos distintos para visualizar los salarios de los empleados:

- Gráfico de barras
- Tablas
- Big number

### Gráficos de barras

El gráfico de **barras** mostrará el salario de cada empleado. Dirígete a `Charts` en el menú y haz click en el botón `+ CHART`.

- Selecciona el dataset `Employees' salaries`.
- Selecciona `Bar Chart`.
- Haz click en el botón `CREATE NEW CHART`.

En la configuración del gráfico:

- Selecciona la columna **full name** en el campo `X-AXIS`.
- Selecciona la columna **salary** en el campo `METRICS` con la agregación `SUM`.

![Bar Chart Configuration](https://docs.jmix.io/jmix/superset/_images/sum-salary.png)

- Haz click en el botón `CREATE CHART` y verás el siguiente resultado:

![Bar Chart Result](https://docs.jmix.io/jmix/superset/_images/bar-chart.png)

Establece como nombre para este gráfico `Salary by employee` y guárdalo sin añadirlo a ningún dashboard.
 
### Tablas

Los gráficos de **tablas** mostrarán el salario medio de cada departamento. Dirígete a **Charts** en el menú y crea un nuevo gráfico haciendo click en el botón `+ CHARTS`.

- Selecciona el dataset `Employees' salaries`.
- Selecciona `Table chart`.
- Haz click en el botón `CREATE NEW CHART`.

En la configuración del gráfico:

- Selecciona la columna **department_name** en el campo `DIMENSIONS`.

Crea una agregación con la columna `salary`:

- Haz click en el campo `METRICS`.
- Selecciona el apartado `SIMPLE`, elige la agregación `AVG` para la columna `salary` y guarda los cambios.

![Table Chart Configuration](https://docs.jmix.io/jmix/superset/_images/avg-salary.png)

- Haz click en el botón `CREATE CHART` y verás el siguiente resultado:

![Table Chart Result](https://docs.jmix.io/jmix/superset/_images/table-chart.png)

Establece como nombre para este gráfico `Salary by department` y guárdalo sin añadirlo a ningún dashboard.

### Big Number

Los gráficos **Big Number** se utiliza para mostrar un único valor. En este caso mostrará la media de salario de todos los empleados.

Dirígete a **Charts** en el menú y crea un nuevo gráfico haciendo click en el botón `+ CHARTS`.

- Selecciona el dataset `Employees' salaries`.
- Selecciona `Big Number`.
- Haz click en el botón `CREATE NEW CHART`.

En la configuración del gráfico:

- Selecciona la columna **department_name** en el campo `DIMENSIONS`.

Crea una agregación con la columna `salary`:

- Selecciona la columna `salary` en el campo `METRICS`.
- Elige la agregación `AVG` y guarda los cambios.

![Big Number Chart Configuration](https://docs.jmix.io/jmix/superset/_images/avg-salary.png)

- En el campo `SUBHEADER` introduce `Employees' AVG salary`.
- Haz click en el botón `CREATE CHART` y verás el siguiente resultado:

![Big Number Chart Result](https://docs.jmix.io/jmix/superset/_images/big-number-chart.png)

Establece como nombre para este gráfico `Employees' AVG salary` y guárdalo sin añadirlo a ningún dashboard.
