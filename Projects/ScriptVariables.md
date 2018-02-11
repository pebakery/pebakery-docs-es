# Sección de script [Variables]

Esta sección contiene las variables y macros predefinidas a las que el script debe hacer referencia. Las variables se cargan en la memoria cuando el script se procesa durante una compilación, se llama a una sección dentro del script mediante el comando `Exec`, o cuando otro script las carga con el comando `AddVariables`.

Esta documentación se refiere a la sección `Variables` ubicada dentro de los archivos `.script`. Para la documentación relacionada con la sección `Variables` para` script.project`, consulte `Project Variables`.

## Sintaxis

Las variables de script y las macros se definen con el formato estilo .INI `Key=Value` `(Clave=Valor)`. Las variables deben estar encerradas en signos de porcentaje `%`.

### Variables

```pebakery
%myProgramName%="My Program"
```

### Macros

```pebakery
myMacro=Run,%PluginFile%,DoSomething
```

## Observaciones

Ninguna.

## Relacionado

[AddVariables](/Commands/Control/AddVariables.md), [Exec](/Commands/Branch/Exec.md), [Project Main](./ProjectMain.md), [Project Process](./ProjectProcess.md), [Project Variables](./ProjectVariables.md), [Script Interface](./ScriptInterface.md), [Script Main](./ScriptMain.md), [Script Process](./ScriptProcess)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=Variables Section
Description=Sección de variables Ejemplo
Author=Homes32
Level=5
Version=1

[Variables]
%myProgramName%="My Program"
myMacro=Run,%ScriptFile%,EchoMessage

[Process]
myMacro,%myProgramName%

[EchoMessage]
Echo,#1
Message,#1
```
