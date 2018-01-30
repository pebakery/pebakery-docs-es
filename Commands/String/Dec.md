# StrFormat,Dec

Disminuye un número o letra por un valor de *n*.

## Sintaxis

```pebakery
StrFormat,Dec,<%DestVar%>,<Integer>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| DestVar | La variable que contiene el valor para disminuir. |
| Integer | Disminuir el valor de `DestVar` por `Integer`. |

## Observaciones

El resultado de la operación será escrito de nuevo en `%DestVar%`.

Este comando admite letras del alfabeto, así como enteros, lo que le permite desplazarse por un rango de letras de unidad (drive).

`Integer` debe ser un valor positivo Si necesita incrementar un número o letra de unidad use `StrFormat,Inc`.

## Relacionado

[Loop](../Branch/Loop.md), [Math,Add](../Math/Add.md), [Math,Sub](../Math/Sub.md), [StrFormat,Inc](./Inc.md)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=StrFormat-Dec Ejemplo
Description=Mostrar el uso de StrFormat,Dec.
Level=5
Version=1
Author=Homes32

[variables]
%int%=10
%letter%=Z

[process]
StrFormat,Dec,%int%,5
StrFormat,Dec,%letter%,1
Message,"Dec [10] por [5] = [%int%]#$xDec [Z] por [1] = [%letter%]"
```
