# Sección de script [Process] (Proceso)

Esta sección contiene la lógica principal del script.

Los comandos colocados en esta sección se ejecutarán durante la compilación de un proyecto o cuando se presione el botón `Ejecutar` en las secuencias de comandos Interfaz gráfica de usuario.

Esta documentación se refiere a la sección `Proceso` ubicada dentro de los archivos `.script`. Para la documentación relacionada con la sección `Proceso` para `script.project`, consulte `Project Process`.

## Observaciones

Ninguna.

## Relacionado

[Project Main](./ProjectMain.md), [Project Process](./ProjectProcess.md), [Project Variables](./ProjectVariables.md), [Script Interface](./ScriptInterface.md), [Script Main](./ScriptMain.md), [Script Variables](./ScriptVariables.md)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=My App Script
Description=Agrega myApp al proyecto.
Author=Homes32
Credits=¡Gracias a ied206 por crear PEBakery!
Selected=True
Level=5
Version=1

[Variables]

[Process]
Message,"¡Hola Mundo!"
```
