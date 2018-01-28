# Math,ToUnSign

Convierte un entero con signo en un entero sin signo.

## Sintaxis

```pebakery
Math,ToUnsign,<%DestVar%>,<Integer>[,Size]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| DestVar | La variable donde se almacenará el resultado. |
| Integer | El entero que se convertirá a entero sin signo. |
| Size | **(Opcional)** Tamaño del número en bits: `8` `16` `32` `64` |

## Observaciones

Ninguna.

## Relacionado

[ToSign](./ToSign.md)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=Math-ToUnsign Ejemplo
Description=Mostrar el uso del comando Math,ToUnsign
Author=Homes32
Level=5

[Variables]

[Process]
Math,ToUnSign,%result%,-32768
Message,"%result%"
```
