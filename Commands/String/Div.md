# StrFormat,Div

Divide dos números.

**Este comando ha quedado obsoleto y puede eliminarse en una versión futura. Se recomienda que actualice su código para usar `Math,Div` tan pronto como sea posible para evitar romper su script.**

## Sintaxis

```pebakery
StrFormat,Div,<%DestVar%>,<Integer>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| DestVar | Variable que contiene el número a dividir. |
| Integer | El número para dividir `DestVar` por. |

## Observaciones

The result of the operation will be written back into `%DestVar%`.

## Relacionado

[StrFormat,Mult](./Mult.md), [Math,Div](../Math/Div.md), [Math,IntDiv](../Math/IntDiv.md), [Math,Mul](../Math/Mul.md)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=StrFormat-Div Example
Description=Mostrar el uso del comando StrFormat,Div
Author=Homes32
Level=5

[Variables]
%int%=20

[Process]
StrFormat,Div,%int%,10
Message,"20 / 10 = %int%"
```
