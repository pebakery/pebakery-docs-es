# Exec

Ejecuta los comandos encontrados en un nombre `[Sección]` (`[Section]`) de un archivo de script.

Puede ejecutar secciones desde cualquier script incluyendo el script desde el cual `Exec` fue originalmente llamado. Todas las variables de la sección `[variables]` del script especificado se agregarán al alcance del script actual. Si existen nombres de variables duplicados, las variables en el script actualmente en ejecución se sobrescribirán.

## Sintaxis

```pebakery
Run,<FileName>,<Section>[,Parameters]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| FileName | La ruta completa del script. Insinuación: Use %scriptFile% para hacer referencia al script actual. |
| Section | El nombre de la sección que contiene los comandos que desea ejecutar. |
| Parameters | **(Opcional)** Parámetros para pasar a la 'Sección' que se está ejecutando. |

### Tokens

Los siguientes tokens se pueden usar para realizar operaciones adicionales cuando se ejecuta una sección.

| Token | Descripción |
| --- | --- |
| #1, #2, #3, etc. | Usado dentro de una 'Sección' para acceder a cualquier parámetro pasado. El esquema de numeración comienza desde `1` y continúa en el orden en que se pasaron los parámetros. Estos tokens se descartan cuando la sección finaliza el procesamiento. |
| #a | Contiene la cantidad de parámetros pasados a `Sección`. |
| #r | Devuelve un valor de la 'Sección'. El token `# r` no se ve afectado por las restricciones de` System,SetLocal` y puede usarse para devolver el valor de una variable aislada al proceso principal. #r es volátil, por lo que si necesita conservar el valor de retorno, cópielo en una variable local. |

## Observaciones

PEBakery permite pasar un número ilimitado de parámetros a la `[Sección]` que se está ejecutando. Esto nos permite crear "funciones" dinámicas que contienen comandos que necesitan ser llamados repetidamente con diferentes argumentos, o utilizados para crear un `Macro`.

Aunque los parámetros mismos se pasan por valor usando tokens, todas las variables están en el alcance de todo el script, por lo que los valores originales pueden modificarse haciendo referencia a ellos por su nombre. Si es necesario, puede usar el comando `System,SetLocal` para aislar las variables modificadas dentro de la sección de ejecución.

## Relacionado

[Run](./Run.md), [SetMacro](../Control/SetMacro.md), [System,SetLocal](../System/SetLocal.md), [System,EndLocal](../System/EndLocal.md)

## Ejemplos

### Ejemplo 1

En este ejemplo usaremos `Exec` para ejecutar un comando en otro script.

#### Script #1 (script1.script)

```pebakery
[Main]
Title=Exec Ejemplo Script #1
Description=Mostrar el uso del comando Exec con un parámetro.
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

// utilizando Run el valor de %file% se tomará de este script (C:\Temp\myFile.txt)
Run,%ProjectDir%\script2.script,Open-File

// utilizando Exec, el valor de %file% se sobrescribirá con el valor tomado de script2 (C:\Temp\myFile2.txt)
Exec,%ProjectDir%\script2.script,Open-File
```

#### Script #2 (Script2.script)

```pebakery
[Main]
Title=Exec Ejemplo Script #2
Description=Mostrar el uso del comando Exec con un parámetro.
Level=5
Version=1
Author=Homes32

[variables]
%file%=C:\Temp\myFile2.txt

[process]

[Open-File]
Message,"Opening file: %file%"
ShellExecute,Open,notepad.exe,%file%
```
