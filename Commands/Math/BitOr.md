# Math,BitOr

Realiza una operación O bit a bit.

## Sintaxis

```pebakery
Math,BitOr,<%DestVar%>,<Vaue1>,<Value2>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| DestVar | La variable donde se almacenará el resultado. |
| Value1 | El primer valor. |
| Value2 | El segundo valor. |

## Observaciones

Ninguna.

## Relacionado

[BitAnd](./BitAnd.md), [BitNot](./BitNot.md), [BitXor](./BitXor.md)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=Math-BitOr Ejemplo
Description=Mostrar el uso del comando Math,BitOr
Author=Homes32
Level=5

[Variables]

[Process]
Math,BitOr,%result%,13,7

// Resultado de salida
Message,"Bitwise OR:#$x#$x00001101 (13)#$x00000111 (7)#$x--------------#$x00001111 (15)#$x#$xReturn: %result%"
```
