# Math,BoolNot

Realiza una prueba No en dos valores booleanos.

## Sintaxis

```pebakery
Math,BoolNot,<%DestVar%>,<Vaue>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| DestVar | La variable donde se almacenará el resultado. |
| Value | El valor para operar en. |

## Observaciones

Ninguna.

## Relacionado

[BoolAnd](./BoolAnd.md), [BoolOr](./BoolOr.md), [BoolXor](./BoolXor.md)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=Math-BoolNot Ejemplo
Description=Mostrar el uso del comando Math,BoolNot
Author=Homes32
Level=5

[Variables]

[Process]
Math,BoolNot,%result1%,True
Math,BoolNot,%result2%,False

// Resultado de salida
Message,"Boolean Not Comparison:#$x[True] Return: %result1%#$x[False] Return: %result2%"
```
