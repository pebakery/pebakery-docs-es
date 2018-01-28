# Math,Div

Divide dos números.

## Sintaxis

```pebakery
Math,Div,<%DestVar%>,<Value1>,<Value2>
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

[IntDiv](./IntDiv.md), [StrFormat,Div](../String/Div.md)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=Math-Div Ejemplo
Description=Mostrar el uso del comando Math,Div
Author=Homes32
Level=5

[Variables]

[Process]
Math,Div,%quot%,20,10
Message,"20 / 10 = %quot%"
```
