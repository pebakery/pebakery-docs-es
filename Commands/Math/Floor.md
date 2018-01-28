# Math,Floor

Devuelve un número redondeado al entero inferior más cercano.

## Sintaxis

```pebakery
Math,Floor,<%DestVar%>,<Value>,<Unit>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| DestVar | La variable donde se almacenará el resultado. |
| Value | El número para redondear hacia abajo. |
| Unit | Unidad para redondear hacia abajo. (ejem. Más cercano 10, 20, 100, etc) |

## Observaciones

Los tamaños de archivo se pueden redondear hacia abajo al más cercano Kb/MB/Gb/Tb/Pb utilizando `StrFormat,Floor`.

## Relacionado

[Ceil](./Ceil.md), [Round](./Round.md), [StrFormat,Floor](../String/Floor.md)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=Math-Floor Ejemplo
Description=Mostrar el uso del comando Math,Floor
Author=Homes32
Level=5

[Variables]

[Process]
Math,Floor,%result%,32,10
Message,"32 redondeado ABAJO al más cercano 10 = %result%"
```
