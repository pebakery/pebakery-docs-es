# Math,IntDiv

Divide dos enteros y devuelve el cociente y el resto.

## Sintaxis

```pebakery
Math,IntDiv,<%QuotientVar%>,<%RemainderVar%>,<Value1>,<Value2>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| QuotientVar | The variable where the result will be stored. |
| RemainderVar | The variable where the remainder will be stored. |
| Value1 | The first value  in the equation. |
| Value2 | The second value in the equation. |

## Observaciones

Ninguna.

## Relacionado

[Div](./Div.md), [StrFormat,Div](../String/Div.md)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=Math-IntDiv Ejemplo
Description=Mostrar el uso del comando Math,IntDiv
Author=Homes32
Level=5

[Variables]

[Process]
Math,IntDiv,%quot%,%remain%,634,37
Message,"634 / 37 = %quot% r. %remain%"
```
