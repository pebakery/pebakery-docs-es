# StrFormat,Mult

Multiplica dos números.

**Este comando ha quedado obsoleto y puede eliminarse en una versión futura. Se recomienda que actualice su código para usar `Math,Mul` tan pronto como sea posible para evitar romper su script.**

## Sintaxis

```pebakery
StrFormat,Mult,<%DestVar%>,<Integer>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| DestVar | Variable que contiene el número a multiplicar. |
| Integer | El número para multiplicar `DestVar` por. |

## Observaciones

El resultado de la operación será escrito de nuevo en `%DestVar%`.

## Relacionado

[StrFormat,Div](./Div.md), [Math,Div](../Math/Div.md), [Math,Mul](../Math/Mul.md)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=StrFormat-Mult Ejemplo
Description=Mostrar el uso del comando StrFormat,Mult
Author=Homes32
Level=5

[Variables]
%int%=20

[Process]
StrFormat,Mult,%int%,10
Message,"20 * 10 = %int%"
```
