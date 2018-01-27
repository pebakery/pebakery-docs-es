# Run

Ejecuta los comandos que se encuentran en una `[Sección]` nombrada de un archivo script.

Puede ejecutar secciones desde cualquier secuencia de comandos, incluida la secuencia de comandos desde donde originalmente se ejecuta `Ejecutar`, pero solo las variables en el alcance de la secuencia de comandos actual serán visibles para la sección que se está ejecutando.

## Sintaxis

```pebakery
Run,<FileName>,<Section>[,Parameters]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| FileName | La ruta completa del script Sugerencia: utilice %ScriptFile% para hacer referencia al script actual. |
| Section | El nombre de la sección que contiene los comandos que desea ejecutar. |
| Parameters | **(Opcional)** Parámetros para pasar a la 'Sección' que se está ejecutando. |

### Tokens

Los siguientes tokens se pueden usar para realizar operaciones adicionales cuando se ejecuta una sección.

| Token | Descripción |
| --- | --- |
| #1, #2, #3, etc. | Usado dentro de una 'Sección' para acceder a cualquier parámetro pasado. El esquema de numeración comienza desde `1` y continúa en el orden en que se pasaron los parámetros. Estos tokens se descartan cuando la sección finaliza el procesamiento. |
| #a | Contiene la cantidad de parámetros pasados a `Sección`. |
| #r | Devuelve un valor de la `Sección`. El token `#r` no se ve afectado por las restricciones de` System,SetLocal` y puede usarse para devolver el valor de una variable aislada al proceso principal. #r es volátil, por lo que si necesita conservar el valor de retorno, cópielo en una variable local. |

## Observaciones

PEBakery permite pasar un número ilimitado de parámetros a la `[sección]` que se está ejecutando. Esto nos permite crear "funciones" dinámicas que contienen comandos que necesitan ser llamados repetidamente con diferentes argumentos, o utilizados para crear una `Macro`.

Aunque los parámetros mismos se pasan por valor usando tokens, todas las variables están en el alcance de todo el script, por lo que los valores originales pueden modificarse haciendo referencia a ellos por su nombre. Si es necesario, puede usar el comando `System,SetLocal` para aislar las variables modificadas dentro de la sección de ejecución.

## Relacionado

[Exec](./Exec.md), [SetMacro](../Control/SetMacro.md), [System,SetLocal](../System/SetLocal.md), [System,EndLocal](../System/EndLocal.md)

## Ejemplos

### Ejemplo 1

En este ejemplo, usaremos el comando `Ejecutar` (`Run`) para organizar el código en secciones que se ejecutarán en función del valor de una casilla de verificación. Esta puede ser una alternativa útil a los bloques de comando `If-Else` si tienes una gran cantidad de comandos para ejecutar.

```pebakery
[Main]
Title=Run Ejemplo 1
Description=Mostrar el uso del comando Ejecutar (Run)
Level=5
Version=1
Author=Homes32

[variables]

[process]
If,%pCheckBox1%,Equal,True,Run,%ScriptFile%,Register-Files
If,%pCheckBox2%,Equal,True,Run,%ScriptFile%,Copy-Files

[Register-Files]
// Hacer algo...
Message,"Registering Files...",INFORMATION,5

[Copy-Files]
// Hacer algo...
Message,"Copying Files...",INFORMATION,5

[Interface]
pCheckBox1="Register Some Files",1,3,10,14,143,18,False
pCheckBox2="Copy files",1,3,10,36,142,18,True
```

### Ejemplo 2

En este ejemplo usaremos el comando `Run` junto con un parámetro para ejecutar una sección.

```pebakery
[Main]
Title=Run Ejemplo 2
Description=Mostrar el uso del comando Run con un parámetro.
Level=5
Version=1
Author=Homes32

[variables]
%file%=C:\Temp\myFile.txt

[process]

If,Not,ExistFile,%file%,Begin
  FileCreateBlank,%file%
  TXTAddLine,%file%,"Hello World!",Append
End

Run,%ScriptFile%,Open-File,%file%

[Open-File]
Echo,"Opening file: #1"
ShellExecute,Open,notepad.exe,#1
```
