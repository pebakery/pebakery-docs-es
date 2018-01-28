# Math,Pow

Eleva un número a una potencia.

## Sintaxis

```pebakery
Math,Pow,<%DestVar%>,<Base>,<PowerOf>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| DestVar | La variable donde se almacenará el resultado. |
| Base | Número base para elevar. |
| PowerOf | La potencia a la que se elevará la `Base`. |

## Observacioness

Ninguna.

## Relacionado

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=Math-Pow Ejemplo
Description=Mostrar el uso del comando Math,Pow
Author=Homes32
Level=5

[Variables]

[Process]
Math,Pow,%result%,2,4
Message,"2^4 = %result%"
```
