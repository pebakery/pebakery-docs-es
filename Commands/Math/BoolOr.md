# Math,BoolOr

Realiza una prueba O en dos valores booleanos.

Se obtiene un resultado verdadero si cualquiera de los valores es verdadero.

## Sintaxis

```pebakery
Math,BoolOr,<%DestVar%>,<Vaue1>,<Value2>
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

[BoolAnd](./BoolAnd.md), [BoolNot](./BoolNot.md), [BoolXor](./BoolXor.md)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=Math-BoolOr Ejemplo
Description=Mostrar el uso del comando Math,BoolOr
Author=Homes32
Level=5

[Variables]

[Process]
Math,BoolOr,%result1%,True,True
Math,BoolOr,%result2%,True,False
Math,BoolOr,%result3%,False,True
Math,BoolOr,%result4%,False,False

// Resultado de salida
Message,"Boolean OR Comparison:#$x[True/True] Return: %result1%#$x[True/False] Return: %result2%#$x[False/True] Return: %result3%#$x[False/False] Return: %result4%"
```
