# If

Ejecutar condicionalmente una declaración.

## Sintaxis

```pebakery
If,<Condition>,<Command>
```

```pebakery
If,<Condition>,Begin
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

## Observaciones

`If` declaraciones y bloques pueden ser anidados.

## Relacionado

[If-Else](./If-Else.md), [If-Question](./If-Question.md)

## Ejemplos

### Ejemplo 1

```pebakery
[main]
Title=If Ejemplo
Description=Demostrar cómo ejecutar declaraciones condicionales usando If.
Level=5
Version=1
Author=Homes32

[variables]

[process]
// Declaración única If. Creará un archivo de texto si aún no existe.
If,Not,ExistFile,C:\Temp\myFile.txt,FileCreateBlank,C:\Temp\myFile.txt

// If declaración usando un bloque de comando para ejecutar múltiples comandos si la declaración se evalúa como Verdadera.
If,ExistFile,C:\Temp\myFile.txt,Begin
  TXTAddLine,C:\Temp\myFile.txt,"Hello World!",APPEND
  ShellExecute,Open,C:\Temp\myFile.txt
End
```
