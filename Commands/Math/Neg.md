# Math,Neg

Devuelve la inversa aritmética de un valor.

## Sintaxis

```pebakery
Math,Neg,<%DestVar%>,<Value>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| DestVar | La variable donde se almacenará el resultado. |
| Value | El valor a invertir. |

## Observaciones

Ninguna.

## Relacionado

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=Math-Neg Ejemplo
Description=Mostrar el uso del comando,Neg Command
Author=Homes32
Level=5

[Variables]

[Process]
Math,Neg,%neg%,32
Message,"32: %neg%"
Math,Neg,%neg%,-32
Message,"-32: %neg%"
```
