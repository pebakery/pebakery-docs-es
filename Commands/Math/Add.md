# Math,Add

Agrega dos números.

## Sintaxis

```pebakery
Math,Add,<%DestVar%>,<Value1>,<Value2>
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

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=Math-Add Ejemplo
Description=Mostrar el uso del comando Math,Add
Author=Homes32
Level=5

[Variables]

[Process]
Math,Add,%sum%,10,20
Message,"10 + 20 = %sum%"
```
