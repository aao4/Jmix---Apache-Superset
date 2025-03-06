# Jmix Superset

## Índice
1. [Introducción](Superset.md#Introducción)
2. [Configuración](Superset_config.md#Configuración)
3. [Dataset](Superset_dataset.md#Dataset)
4. [Gráficos](Superset_graficos.md#Gráficos)
5. [Dashboard](Superset_dashboard.md#Dashboard)
6. [Problemas](Superset_problems.md#problema-bucle-infinito-building-front-end-development-bundle-en-jmix-con-intellij-idea)

## Introducción
Apache Superset es una aplicación web que permite explorar, visualizar y compartir datos de manera rápida y eficiente mediante dashboards interactivos.

Superset es un complemento que facilita la integración de aplicaciones Jmix con Apache Superset, permitiendo añadir dashboards interactivos en las vistas de la aplicación. Gracias al componente `SupersetDashboard` y sus funciones asociadas, es posible mostrar dashboards creados en Apache Superset en las vistas de nuestra aplicación.

Para incorporar un dashboard, solo debes configurar la URL y las credenciales de Superset, y agregar el componente `SupersetDashboard` a la vista.

![Superset Preview](https://docs.jmix.io/jmix/superset/_images/overview-embedded-dashboard.png)

## Instalación

### Instalación automática
Para instalar automáticamente a través de `Jmix Marketplace`, deberás dirigirte a la ventana de Jmix de tu proyecto.

Abre el menú de configuración de dicha ventana y selecciona `Marketplace`. 

![Superset Marketplace](https://docs.jmix.io/jmix/_images/addons/toolbar.png)

Una vez ahí, busca el complemento (add-on) `Superset` e instálalo.

Selecciona **Apply Changes & close**.

### Instalación manual
Para la instalación manual, agrega las siguientes dependencias a tu archivo `build.gradle`:

```gradle
dependencies {
    implementation 'io.jmix.superset:jmix-superset-starter'
    implementation 'io.jmix.superset:jmix-superset-flowui-starter'
}
```
