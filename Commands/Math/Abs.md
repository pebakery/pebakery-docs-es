# Math,Abs

Calcula el valor absoluto de un número.

## Sintaxis

```pebakery
Math,Abs,<%DestVar%>,<Value>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| DestVar | La variable donde se almacenará el resultado. |
| Value | Número. |

## Observaciones

Ninguna.

## Relacionado

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=Math-Abs Ejemplo
Description=Mostrar el uso del Comando Math,Abs
Author=Homes32
Level=5

[Variables]

[Process]
Math,Abs,%result%,-32
Message,"Valor absoluto de -32 = %result%"
```
