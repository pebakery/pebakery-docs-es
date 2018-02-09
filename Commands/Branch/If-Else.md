# If-Else

Declaraciones condicionalmente ejecutadas.

## Sintaxis

```pebakery
If,<Condition>,<Command>
Else,<AltCommand>
```

```pebakery
If,<Condition>,Begin
 <Command>
 ...
 <Command>
End
Else,Begin
 <Command>
 ...
 <Command>
End
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| Condition | Condición para evaluar como `True` o` False`. |
| Command | El comando que se ejecutará si la condición es `True`. |
| AltCommand | El comando que se ejecutará si la condición es `False`. |

## Observaciones

`If-Else` las declaraciones y los bloques se pueden anidar.

## Relacionado

[If-Else](./If-Else.md), [If-Question](./If-Question.md)

## Ejemplos

### Ejemplo 1

```pebakery
[main]
Title=If-Else Ejemplo
Description=Demostrar cómo ejecutar declaraciones condicionales usando If-Else.
Level=5
Version=1
Author=Homes32

[variables]

[process]
// Declaración única If-Else. Creará un archivo de texto si aún no existe.
If,Not,ExistFile,C:\Temp\myFile.txt,Message,"El archivo no existe",INFORMATION
Else,Message,"El archivo ya existe",INFORMATION

// Instrucción If-Else utilizando un bloque de comandos para ejecutar comandos múltiples.
If,ExistFile,C:\Temp\myFile.txt,Begin
  TXTAddLine,C:\Temp\myFile.txt,"¡Adiós mundo!",APPEND
End
Else,Begin
  FileCreateBlank,C:\Temp\myFile.txt
  TXTAddLine,C:\Temp\myFile.txt,"¡Hola Mundo!",APPEND
End

ShellExecute,Open,C:\Temp\myFile.txt
```
