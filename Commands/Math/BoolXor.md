# Math,BoolXor

Realiza una prueba O exclusiva en dos valores booleanos.

Se obtiene un resultado verdadero si uno, y solo uno, de los valores es verdadero.

## Sintaxis

```pebakery
Math,BoolXor,<%DestVar%>,<Vaue1>,<Value2>
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

[BoolAnd](./BoolAnd.md), [BoolNot](./BoolNot.md), [BoolOr](./BoolOr.md)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=Math-BoolXor Ejemplo
Description=Mostrar el uso del comando Math,BoolXor
Author=Homes32
Level=5

[Variables]

[Process]
Math,BoolXor,%result1%,True,True
Math,BoolXor,%result2%,True,False
Math,BoolXor,%result3%,False,True
Math,BoolXor,%result4%,False,False

// Resultado de salida
Message,"Boolean XOR Comparison:#$x[True/True] Return: %result1%#$x[True/False] Return: %result2%#$x[False/True] Return: %result3%#$x[False/False] Return: %result4%"
```
