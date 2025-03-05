# Jmix Superset

## Índice
1. [Introducción](Superset.md#Introducción)
2. [Configuración](Superset_config.md#Configuración)
3. [Dataset](Superset_dataset.md#Dataset)
4. [Gráficos](Superset_graficos.md#Gráficos)
5. [Dashboard](Superset_dashboard.md#Dashboard)

## Dashboard

### Crear Dashboard

Un dashboard o tablero es un espacio unificado en el que se pueden desplegar múltiples gráficos. Se pueden personalizar dándole un tamaño a los gráficos, reorganizar su diseño y agregar nuevos gráficos.

En esta sección crearás un dashboard en Superset que contendrá los gráficos que hemos creado anteriormente en el apartado [Gráficos](Superset_graficos.md#Gráficos) y lo incrustaremos en la aplicación de Jmix.

Para crear un nuevo dashboard, dirígete a `Dashboards` en el menú y haz click en el botón `+ DASHBOARD`. Verás los grádicos creados anteriormente.

- Agrega los gráficos que hemos creado anteriormente en el siguiente orden:

![Dashboard Create](https://docs.jmix.io/jmix/superset/_images/dashboard.png)

- Introduce como nombre del dashboard `Employees' salaries` y guárdalo.

Después de guardarlo, deberemos configurar los ajustes para hacer que este se pueda incrustar.

- Haz click en el botón de ajustes en la esquina de arriba a la izquierda y selecciona `Embed dashboard`.

![Embed Dashboard](https://docs.jmix.io/jmix/superset/_images/dashboard-settings.png)

- Haz click en el botón `ENABLE EMBEDDING`. Esto generará un `embedded ID` de este dashboard para que lo puedas utilizar en la aplicación de Jmix.

![Dashboard Embedded ID](https://docs.jmix.io/jmix/superset/_images/embedded-id-dialog.png)

### Incrustar Dashboard en la aplicación de Jmix

Para mostrar el dashboard que hemos creado en Jmix deberemos utilizar el componente `SupersetDashboard`. Este componente requiere el `embedded ID` que hemos generado previamente en la configuración del dashboard.

- Crea una nueva vista llamada `Salaries dashboard` usando la plantilla `Blank view`.
- Añade el componente `SupersetDashboard` mediante la opción `Add Component`.

![Dashboard Jmix Config](https://docs.jmix.io/jmix/superset/_images/adding-dashboard.png)

- Configura los atributos `id`, `height` y `width` del elemento `superset:dashboard`:

    - `id` = `dashboard`
    - `height` = `100%`
    - `width` = `100%`

- Copia el ID del dashboard de Superset y añadelo al atributo `embeddedId`.

Resultado del codigo XML:

```xml
<superset:dashboard id="dashboard"
                    width="100%"
                    height="100%"
                    embeddedId="940f36ff-6c97-4a35-a4ff-4e4aeee3a9c7"/>
```

- Cuando hayas terminado este paso, reinicia la aplicación o realiza un hot deploy de los cambios que has hecho en la vista y refresca la página.

Finalmente, el resultado de este tutorial será una vista en la que podemos ver el dashboard de Superset en nuestra aplicación de Jmix:

![Dashboard Jmix Result](https://docs.jmix.io/jmix/superset/_images/embeded-dashboard.png)
