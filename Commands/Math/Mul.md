# Math,Mul

Multiplica dos números.

## Sintaxis

```pebakery
Math,Mul,<%DestVar%>,<Value1>,<Value2>
```

### Argumentos

| Argumento | Description |
| --- | --- |
| DestVar | La variable donde se almacenará el resultado. |
| Value1 | El primer valor en la ecuación. |
| Value2 | El segundo valor en la ecuación. |

## Observaciones

None.

## Ninguna

[StrFormat,Mult](../String/Mult.md)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=Math-Mul Ejemplo
Description=Mostrar el uso del comando the Math,Mul
Author=Homes32
Level=5

[Variables]

[Process]
Math,Mul,%prod%,20,10
Message,"20 * 10 = %prod%"
```
