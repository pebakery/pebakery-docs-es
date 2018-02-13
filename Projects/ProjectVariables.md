# Sección del proyecto [Variables]

Esta sección contiene las variables y macros GLOBALES a las que los scripts del proyecto deben hacer referencia. Las variables se cargan en la memoria cuando se inicia una compilación o un script se ejecuta manualmente y están disponibles para todos los scripts en el proyecto.

Esta documentación se refiere a la sección `Variables` ubicada dentro del archivo `script.project`. Para la documentación relacionada con la sección 'Variables' de los scripts individuales, consulte `Script Variables'.

## Sintaxis

Las variables globales y las macros se definen con el formato estilo .INI `Key=Value` `(Clave=Valor)`. Las variables deben estar encerradas en signos de porcentaje `%`.

### Variables

```pebakery
%myGlobalVar%="C:\Temp"
```

### Variables API

Las siguientes variables se pueden usar dentro de la sección Variables de _script.project_ para definir una "Macro Library" personalizada que estará disponible para todo el proyecto.

| Variable | Descripción |
| --- | --- |
| %API% | La ruta completa a un archivo de script que contiene una "Macro Library" ("Biblioteca de macros"). |
| %APIVAR% | El nombre de la sección dentro del script definido por `%API%` que contiene las definiciones de macro que se cargarán en el alcance del proyecto GLOBAL. |

### Macros

```pebakery
myMacro=Run,%PluginFile%,DoSomething
```

## Observaciones

Nota: con Winbuilder fue necesario cargar una "Biblioteca de macros" al colocar el comando `AddVariables,%API%,ApiVar,GLOBAL` en la sección de proceso de _script.project_. En PEBakery esto no es obligatorio. Las macros definidas en la sección `%APIVAR%` del archivo `%API%` se cargarán automáticamente en el ámbito GLOBAL.

## Relacionado

[Project Main](./ProjectMain.md), [Project Process](./ProjectProcess.md), [Script Interface](./ScriptInterface.md), [Script Main](./ScriptMain.md), [Script Process](./ScriptProcess), [Script Variables](./ScriptVariables.md), [Macros](/LangRef/Macros.md)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=myProject
Description=Proyecto de Ejemplo
Author=Homes32
Version=1

[Variables]
%RegSystem%=%TargetDir%\Windows\System32\config\System
%RegSoftware%=%TargetDir%\Windows\System32\config\Software
%RegDefault%=%TargetDir%\Windows\System32\config\Default
%RegComponents%=%TargetDir%\Windows\System32\config\Components
%AutoRunFile%=%TargetDir%\Windows\System32\autorun.cfg
%BootSRC%=D:\PEBakery\Mount\Win10PESE\Source\BootWimSrc
%InstallSRC%=D:\PEBakery\Mount\Win10PESE\Source\InstallWimSrc
%Source_Win%=D:\PEBakery\Mount\Win10PESE\Source\InstallWimSrc\Windows
%Target_Win%=%TargetDir%\Windows
%Source_Sys%=D:\PEBakery\Mount\Win10PESE\Source\InstallWimSrc\Windows\System32
```

### Ejemplo 2

En este ejemplo, definimos un archivo .script llamado _myMacroLibrary.script_ como nuestro script de proyectos "API" y cargamos todas las macros en el alcance global del proyecto.

```pebakery
[Main]
Title=myProject
Description=Proyecto de Ejemplo
Author=Homes32
Version=1

[Variables]
%API%=%ProjectDir%\Build\myMacroLibrary.script
%APIVAR%=MacroDef

```
