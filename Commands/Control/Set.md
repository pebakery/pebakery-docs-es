# Set (Establecer)

Cambia o define el valor de una variable.

## Sintaxis

```pebakery
Set,<%Variable%>,<Value>[,GLOBAL | PERMANENT]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| %Variable% | El nombre de nuestra variable. |
| Value | El valor de la variable. |

### Flags

Las siguientes flags (indicadores) son mutuamente excluyentes.

| Flag | Descripción |
| --- | --- |
| GLOBAL | Almacena la variable en la memoria global durante el tiempo de vida del proceso de compilación. Esto permitirá que otros scripts hagan referencia y/o modifiquen este valor. Si la `Variable` ya está definida, el valor se sobrescribirá. |
| PERMANENT | Almacena permanentemente el valor de esta variable escribiendo la definición en la sección [Variables] de script.project. If the `Variable` is already defined the value will be overwritten. |

## Observaciones

A menos que se definan la flag (indicador) `GLOBAL` o `PERMANENT`, el alcance `%Variable%` se limita al script en ejecución.

Alternativamente, las variables también se pueden definir antes de la ejecución colocando las definiciones en la sección `[Variables]` del script. Ver el Ejemplo 2 para más detalles.

El comando `Set,...,PERMANENT` no se debe usar para cambiar los valores de control de la interfaz. Use el comando `InterfaceWrite` para este propósito.

## Relacionado

[SetMacro](./SetMacro.md), [WriteInterface](../Interface/WriteInterface.md)

## Ejemplos

Define variables durante la ejecución del script.

### Ejemplo 1

```pebakery
[Main]
Title=Variables Ejemplo 1
Description=Mostrar el uso del comando Establecer (Set).
Author=Homes32
Level=5
Version=1

[Variables]

[Process]
Set,%ProgramName%,"myApp"
Set,%DownloadURL%,http://mySite.net/myApp.exe
// Establecer (Set) %isMyAppInstalled% como una variable global para que otros scripts puedan acceder a ella.
Set,%isMyAppInstalled%,True,GLOBAL
// Establecer (Set) %ProjectTemp% = al valor de pFileBox1 y almacenarlo permanentemente en script.project
Set,%BuildSource%,%pFileBox1%,PERMANENT
Echo,%BuildSource%

Echo,"Downloading %ProgramName%"
Webget,%DownloadURL%,C:\Temp


[Interface]
pFileBox1=C:\Images\,1,13,23,44,230,20,dir
pTextLabel1="Seleccione su directorio fuente:",1,1,23,25,230,18,8,Bold
```

### Ejemplo 2

Definir variables antes de la ejecución colocando las definiciones en la sección `[Variables]` del script.

```pebakery
[Main]
Title=Variables Ejemplo 2
Description=Mostrar el uso de la sección variables.
Author=Homes32
Level=5
Version=1

[Variables]
ProgramName=myApp
DownloadURL=http://mySite.net/myApp.exe

[Process]
Echo,"Downloading %ProgramName%"
Webget,%DownloadURL%,C:\Temp
```
