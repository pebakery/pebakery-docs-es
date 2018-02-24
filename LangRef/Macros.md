# Macros

Las macros se definen como los procedimientos que se ejecutarán cuando se encuentre una palabra clave específica.

Las macros simplifican el mantenimiento de los scripts ya que el código se escribe solo una vez, pero se puede invocar repetidamente por cualquier cantidad de scripts o procesos. Son ideales para tareas repetitivas, como crear accesos directos o descargar y desempaquetar un archivo.

## Definiendo una macro

Las macros se pueden definir de diferentes maneras.

1. La sección [Variables] de un _.script_ o _script.project_ file.
1. El comando SetMacro.
1. La definición de interfaz de programación de aplicaciones (API) de los proyectos.

Los nombres de macro solo pueden contener los siguientes caracteres `a-z A-Z 0-9 _ ( )`. Debido a que las macros se analizan antes del tiempo de ejecución utilizando %Variables% en el nombre de la macro no es compatible.

### Definición de una macro con la sección [Variables]

Las macros se definen usando el formato estilo .INI `Key=Value` `(Clave=Valor)`. A diferencia de las variables, el nombre de la macro **no** es encerrado en los signos `%`.

```pebakery
[Variables]
myMacro=Run,%PluginFile%,DoSomething
```

Para más detalles ver [Script Variables](/Projects/ScriptVariables.md) y [Project Variables](/Projects/ProjectVariables.md).

### Definiendo una macro con el comando `SetMacro`

Ver la documentación para el comando [SetMacro](/Commands/Control/SetMacro.md).

### Definiendo una "Macro Library" ("Biblioteca de Macros")

Las siguientes variables se pueden usar dentro de la sección Variables del _script.project_ para definir una "Macro Library" personalizada que estará disponible para todo el proyecto.

| Variable | Descripción |
| --- | --- |
| %API% | La ruta completa a un archivo de script que contiene una "Macro Library". |
| %APIVAR% | El nombre de la sección dentro del script definido por `% API%` que contiene las Definiciones de macro que se cargarán en el alcance del proyecto GLOBAL. |

Para más detalles ver [Project Variables](/Projects/ProjectVariables.md).
