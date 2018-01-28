# Math,BitAnd

Realiza una operación Y a nivel de bit.

## Sintaxis

```pebakery
Math,BitAnd,<%DestVar%>,<Vaue1>,<Value2>
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

[BitNot](./BitNot.md), [BitOr](./BitOr.md), [BitShift](./BitShift.md), [BitXor](./BitXor.md)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=Math-BitAnd Ejemplo
Description=Mostrar el uso del comando Math,BitAnd
Author=Homes32
Level=5

[Variables]

[Process]
Math,BitAnd,%result%,13,7

// Resultado de salida
Message,"Bitwise AND:#$x#$x00001101 (13)#$x00000111 (7)#$x--------------#$x00000101 (5)#$x#$xReturn: %result%"
```
