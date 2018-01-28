# Math,ToSign

Convierte un entero sin signo a un entero con signo.

## Sintaxis

```pebakery
Math,ToSign,<%DestVar%>,<Integer>[,Size]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| DestVar | La variable donde se almacenará el resultado. |
| Integer | El entero sin signo a ser convertido a entero con signo. |
| Size | **(Opcional)** Tamaño del número en bits: `8` `16` `32` `64` |

## Observaciones

Ninguna.

## Relacionado

[ToUnsign](./ToUnsign.md)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=Math-ToSign Ejemplo
Description=Mostrar el uso del comando the Math,ToSign
Author=Homes32
Level=5

[Variables]

[Process]
Math,ToSign,%result%,4294934528
Message,"%result%"
```
