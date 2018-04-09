# Variables

Las variables se utilizan para almacenar un valor en la memoria mientras se procesa un script.

## Declarando variables

Las variables consisten en un nombre único que se usa para identificar la variable y debe estar encerrado en signos de porcentaje `%`. Los nombres de las variables no distinguen entre mayúsculas y minúsculas, por lo que `% myVar%` es lo mismo que `% MYVAR%`.

Las variables se pueden definir de varias maneras diferentes:

Variables predefinidas definidas en la sección [Variables] del script

```pebakery
[Variables]
%myVar%="Hello World!"
```

Dinámicamente en tiempo de ejecución utilizando los comandos `Set` y` AddVariables`

```pebakery
Set,%myVar%,12345
AddVariables,%ScriptFile%,AlternativeVariables
```

Como valor de retorno de un comando como `StrFormat`, `Math` o `RegRead`.

```pebakery
StrFormat,Left,"Hello World!",5,%result%
```

## Orden de búsqueda de variables

Es posible que la variable local pueda compartir el mismo nombre con una variable global del proyecto. En caso de que se produzca una colisión de nombre, se utilizará el siguiente orden para determinar el valor que se utilizará en el script.

### PEBakery estándar

1. Variables fijas
1. Variables locales
1. Variables globales

### Compatible con WinBuilder

Cuando la opción de compatibilidad `Variables fijas reemplazables` está habilitada, se utiliza el siguiente orden de búsqueda.

1. Variables locales
1. Variables globales
1. Variables fijas

## Tipos de variables

### Variables fijas

Las variables fijas son variables reservadas que están pobladas por PEBakery y no se pueden sobrescribir*.

_*La opción de compatibilidad de Winbuilder `Variables fijas anulables` puede habilitarse para compatibilidad con proyectos más antiguos en transición de Winbuilder a PEBakery, sin embargo, se recomienda que el proyecto se actualice lo más rápido posible para eliminar este comportamiento inseguro._

#### Variables de sistema fijas

| Variable | Descripción |
| --- | --- |
| %PEBakery% | Siempre devuelve `TRUE` si el script se ejecuta con PEBakery. Se usa para la compatibilidad entre compiladores con scripts que contienen funciones no implementadas en Winbuilder.  |
| %BaseDir% | El directorio desde el que se lanzó PEBakery. Esta variable se usa ampliamente como un punto de referencia para determinar las rutas relativas de directorios importantes, como `Proyectos`,` Objetivo` y `Caché / Banco de trabajo`. Ex. `% BaseDir%\Target` |
| %Version% | Para la compatibilidad con los scripts diseñados para Winbuilder, esta variable siempre devuelve `082`. |
| %EngineVersion% | Devuelve la versión amigable de la máquina del motor PEBakery. |
| %PEBakeryVersion% | Devuelve la versión amigable para el ser humano del motor PEBakery. |
| %ProjectTitle% | El nombre del proyecto como se define en script.projects `Main` section. |
| %ProjectDir% | La ruta completa al directorio que contiene el proyecto (script.project). |

#### Variables de script fijas

| Variable | Descripción |
| --- | --- |
| %ScriptDir% | La ruta completa al directorio que contiene el script actualmente en ejecución. |
| %ScriptFile% | La ruta completa del script actualmente en ejecución. |
| %ScriptTitle% | El título del script que se está ejecutando actualmente como se define en la sección `[Principal]` del script. |

#### Variables de entorno fijo

Las variables de entorno fijo se incluyen solo para la compatibilidad con Winbuilder y deben habilitarse con la opción de compatibilidad 'Enable Environment Variables'. Si necesita recuperar información sobre el entorno del sistema operativo local, se recomienda utilizar el comando más flexible `System, GetEnv` en su lugar.

| Variable | Descripción |
| --- | --- |
| %ProgramFilesDir% | La ruta del directorio `Program Files` del sistema operativo local. |
| %ProgramFilesDir_x86% | Si La ruta del directorio 'Archivos de programa (x86) `del sistema operativo local (solo sistema operativo x64). |
| %TempDir% | La ruta del directorio `Temp` del sistema operativo local. |
| %UserName% | El nombre del usuario actualmente conectado. |
| %UserProfile% | La ruta del directorio de inicio del usuario conectado. |
| %WindowsDir% | La ruta del directorio `Windows` del sistema operativo local. |
| %WindowsVersion% | El número de versión del sistema operativo local. |

### Variables locales

Las variables locales son "visibles" solo para el script actualmente en ejecución. Todas las variables se crean en el ámbito local a menos que se defina explícitamente de otra manera.

### Variables globales

Las variables globales están disponibles para todo el proyecto y se pueden definir por:

La sección [Variables] de Script.Project

```pebakery
[Variables]
%myVar%=12345
```

La palabra clave `GLOBAL`

```pebakery
Set,%myVar%,12345,GLOBAL
```

#### Variables globales heredadas

Las siguientes variables se incluyen para la compatibilidad con WinBuilder, que las almacena en la sección `[Main]` de `script.project`.

Si `PathSetting=True` se define en` script.project`, las siguientes variables se establecen en el valor de la clave coincidente en la sección `script.project` `[Main]`. Si `PathSetting=False` se ignorarán.

| Variable | Configuración de ruta | Valor |
| --- | :---: | --- |
| %SourceDir% | True | Valor de `SourceDir=` |
| | Falso | indefinido |
| %TargetDir% | True | Valor de `TargetDir=` |
| | Falso | indefinido |
| %ISOFile% | True | Valor de `ISOFile=` |
| | Falso | indefinido |

## Relacionado

[AddVariables](/Commands/Control/AddVariables.md), [Set](/Commands/Control/Set.md), [Project Variables](/Projects/ProjectVariables.md), [Script Variables](/Projects/ScriptVariables.md)
