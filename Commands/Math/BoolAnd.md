# Math,BoolAnd

Realiza una prueba Y en dos valores booleanos.

Un resultado de salida verdadero solo si ambos valores son verdaderos.

## Sintaxis

```pebakery
Math,BoolAnd,<%DestVar%>,<Vaue1>,<Value2>
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

[BoolNot](./BoolNot.md), [BoolOr](./BoolOr.md), [BoolXor](./BoolXor.md)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=Math-BoolAnd Ejemplo
Description=Mostrar el uso del comando Math,BoolAnd
Author=Homes32
Level=5

[Variables]

[Process]
Math,BoolAnd,%result1%,True,True
Math,BoolAnd,%result2%,True,False
Math,BoolAnd,%result3%,False,True
Math,BoolAnd,%result4%,False,False

// Resultado de salida
Message,"Boolean AND Comparison:#$x[True/True] Return: %result1%#$x[True/False] Return: %result2%#$x[False/True] Return: %result3%#$x[False/False] Return: %result4%"
```
