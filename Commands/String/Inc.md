# StrFormat,Inc

Incrementa un número o letra por un valor de *n*.

## Sintaxis

```pebakery
StrFormat,Inc,<%DestVar%>,<Integer>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| DestVar | La variable que contiene el valor a incrementar. |
| Integer | Aumenta el valor de `DestVar` por `Integer`. |

## Observaciones

El resultado de la operación será escrito de nuevo en`%DestVar%`.

Este comando admite letras del alfabeto, así como enteros, lo que le permite recorrer un rango de letras de unidad (drive) lexicográficamente.

`Integer` debe ser un valor positivo Si necesita disminuir un número o utilizar una letra de unidad use `StrFormat,Dec`.

## Relacionado

[Loop](../Branch/Loop.md),[LoopLetter](../Branch/LoopLetter.md), [Math,Add](../Math/Add.md), [Math,Sub](../Math/Sub.md), [StrFormat,Dec](./Dec.md)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=StrFormat-Inc Ejemplo
Description=Mostrar el uso del comando StrFormat,Inc.
Level=5
Version=1
Author=Homes32

[variables]
%int%=10

[process]
StrFormat,Inc,%int%,5
Message,"Inc [10] by [5] = [%int%]"
```

### Ejemplo 2

En este ejemplo usamos `StrFormat,Inc` junto con el comando `Loop` para recorrer las letras de la unidad A-Z buscando notepad.exe.

```pebakery
[Main]
Title=StrFormat-Inc A-Z Ejemplo
Description=Demostrar cómo recorrer las letras de unidad buscando un archivo.
Level=5
Version=2
Author=Homes32

[variables]

[process]
Set,%searchFile%,"Windows\notepad.exe"
Loop,%ScriptFile%,Search-Drives,1,26
If,EXISTFILE,%fullPath%,ShellExecute,OPEN,%fullPath%

[Search-Drives]
Set,%drive%,A
StrFormat,Inc,%drive%,#c
Echo,"Buscando unidad [%drive%:\]"
Set,%fullPath%,%drive%:\%searchFile%
If,EXISTFILE,%fullPath%,Loop,BREAK
```
