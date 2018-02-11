# Sección del proyecto [Process] (Proceso)

Esta sección contiene comandos que se ejecutarán cada vez que se procese un script en el proyecto.

Los comandos colocados en esta sección se ejecutarán durante la compilación de un proyecto o cuando se presione el botón `Ejecutar` en la interfaz gráfica de usuarioed.

Esta documentación se refiere a la sección `Proceso` ubicada dentro del archivo `script.project`. Para obtener documentación relacionada con la sección `Proceso` de scripts individuales, consulte `Script Process`.

## Observaciones

Debido a que esta sección se procesa **cada vez** que se ejecuta un script en el proyecto, el uso de esta sección debe limitarse a las funciones que son de naturaleza Global y son esenciales para el proyecto. De lo contrario, puede ocasionar penalizaciones de rendimiento y tiempos de construcción más lentos.

## Relacionado

[Project Main](./ProjectMain.md), [Project Variables](./ProjectVariables.md), [Script Interface](./ScriptInterface.md), [Script Main](./ScriptMain.md), [Script Process](./ScriptProcess), [Script Variables](./ScriptVariables.md)

## Ejemplos

En este ejemplo usamos la sección de proceso de _script.project_ para definir una función de limpieza usando `System,ONBUILDEXIT`, para asegurar que cualquier sección del registro o imágenes WIM montadas se limpien, incluso si falla una secuencia de comandos y la compilación se detiene.

### Ejemplo 1

```pebakery
[Main]
Title=myProject
Description=Proyecto de Ejemplo
Author=Homes32
Version=1

[Variables]

[Process]
System,ONBUILDEXIT,Exec,%ProjectDir%\script.project,myProject-ONBUILDEXIT

[myProject-ONBUILDEXIT]
// Asegúrese que todas las secciones del Registro esten descargadas.
RegHiveUnload,%RegSystem%
RegHiveUnload,Tmp_Software
RegHiveUnload,%RegDefault%
RegHiveUnload,%RegComponents%
```
