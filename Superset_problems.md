# Jmix Superset

## Índice
1. [Introducción](Superset.md#Introducción)
2. [Configuración](Superset_config.md#Configuración)
3. [Dataset](Superset_dataset.md#Dataset)
4. [Gráficos](Superset_graficos.md#Gráficos)
5. [Dashboard](Superset_dashboard.md#Dashboard)
6. [Problemas](Superset_problems.md#problema-bucle-infinito-building-front-end-development-bundle-en-jmix-con-intellij-idea)

## Problema bucle infinito “Building front-end development bundle” en Jmix con IntelliJ IDEA

Al utilizar Jmix en IntelliJ IDEA, algunos usuarios han reportado que el proceso "Building front-end development bundle" se mantiene en bucle y no finaliza correctamente. Esta guía proporciona una serie de soluciones sugeridas por la comunidad y que han resultado efectivas en otros casos similares.

![Building front-end development bundle image](https://forum.jmix.io/uploads/default/original/2X/b/be6cb801e40a59eb930211c3c34b4f341e453966.png)

## Posibles mensajes en la consola

Cuando ocurre este problema, es posible que en la consola de ejecución se muestren mensajes como los siguientes:

```
2024-07-27T21:32:26.271+04:00 DEBUG 26276 — [nio-8080-exec-2] io.jmix.core.AccessLogger : Denied access to [view: MainView] for user [anonymous] by io.jmix.securityflowui.constraint.UiShowViewConstraint
2024-07-27T21:32:28.973+04:00 INFO 26276 — [onPool-worker-1] c.v.f.s.frontend.TaskUpdatePackages : using ‘C:\Program Files\nodejs\npx.cmd --yes --quiet pnpm --shamefully-hoist=true --ignore-scripts install’ for frontend package installation
```

Estos mensajes pueden indicar que el proceso de instalación o actualización de paquetes front-end está en curso, pero no avanza correctamente.

### Causas potenciales

Este problema puede surgir en situaciones como:

- **Actualización de Jmix**: Al migrar a una versión más reciente, como Jmix 2.3.1.
- **Instalación de complementos**: Al agregar plugins desde el marketplace de Jmix, por ejemplo, el plugin de "Superset Apache".

### Soluciones al problema

1. **Actualizar Node.js a la última versión LTS**:

   Asegúrate de tener Node.js actualizado a la última versión LTS disponible. Esta versión se encuentra en el sitio web oficial: [https://nodejs.org/](https://nodejs.org/).

2. **Eliminar archivos y directorios relacionados con la construcción del front-end**:

    Navega al directorio raíz del proyecto y elimina los siguientes archivos y carpetas:

     ```
     node_modules 
     package.json 
     pnpm-lock.yaml 
     tsconfig.json 
     types.d.ts 
     vite.config.ts 
     vite.generated.ts
     ```

    Además, elimina los directorios `bundles` (ubicado en `src/main`), `build` y `frontend/generated`:

3. **Reconstruir y ejecutar el proyecto**:

   Una vez realizados los pasos anteriores, reconstruye y ejecuta el proyecto desde IntelliJ IDEA.
