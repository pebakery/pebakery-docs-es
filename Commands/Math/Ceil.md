# Math,Ceil

Devuelve un número redondeado al siguiente entero.

## Sintaxis

```pebakery
Math,Ceil,<%DestVar%>,<Value>,<Unit>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| DestVar | La variable donde se almacenará el resultado. |
| Value | El número para redondear hacia arriba . |
| Unit | Unidad para redondear hacia arriba. (por ejemplo, 10, 20, 100, etc.) |

## Observaciones

Los tamaños de archivo se pueden redondear hacia arriba al más cercano Kb/MB/Gb/Tb/Pb utilizando `StrFormat,Ceil`.

## Relacionado

[Floor](./Floor.md), [Round](./Round.md), [StrFormat,Ceil](../String/Ceil.md)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=Math-Ceil Ejemplo
Description=Mostrar el uso del comando Math,Ceil
Author=Homes32
Level=5

[Variables]

[Process]
Math,Ceil,%result%,32,10
Message,"32 redondeado hacia arriba al más cercano 10 = %result%"
```
