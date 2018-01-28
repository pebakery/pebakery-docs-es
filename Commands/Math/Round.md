# Math,Round

Devuelve un entero redondeado al número entero más cercano.

## Sintaxis

```pebakery
Math,Round,<%DestVar%>,<Value>,<Unit>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| DestVar | La variable donde se almacenará el resultado. |
| Value | El número a redondear. |
| Unit | Unidad para redondear a. (ex. Nearest 10, 20, 100, etc) |

## Observaciones

Los tamaños de archivo se pueden redondear al más cercano Kb/MB/Gb/Tb/Pb utilizando `StrFormat,Round`.

## Relacionado

[Ceil](./Ceil.md), [Floor](./Floor.md), [StrFormat,Round](../String/Round.md)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=Math-Round Ejemplo
Description=Mostrar el uso del comando Math,Round
Author=Homes32
Level=5

[Variables]

[Process]
Math,Round,%result%,1024,1000
Message,"1024 redondeado al más cercano 1000 = %result%"
```
