# Math,Sub

Resta dos números.

## Sintaxis

```pebakery
Math,Sub,<%DestVar%>,<Value1>,<Value2>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| DestVar | La variable donde se almacenará el resultado. |
| Value1 | El primer valor en la ecuación. |
| Value2 | El segundo valor en la ecuación. |

## Observaciones

Ninguna.

## Relacionado

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=Math-Sub Ejemplo
Description=Mostrar el uso del comando Math,Sub
Author=Homes32
Level=5

[Variables]

[Process]
Math,Sub,%diff%,30,10
Message,"30 - 10 = %diff%"
```
