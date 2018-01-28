# Math,BitXor

Realiza una operación O exclusiva a nivel de bits.

## Sintaxis

```pebakery
Math,BitXor,<%DestVar%>,<Vaue1>,<Value2>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| DestVar | La variable donde se almacenará el resultado. |
| Value1 | El primer valor. |
| Value2 | El segundo valor. |

## Observaciones

Ninguna.

## Related

[BitAnd](./BoolAnd.md), [BitNot](./BitNot.md), [BitShift](./BitShift.md), [BitOr](./BitOr.md)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=Math-BitXor Ejemplo
Description=Mostrar el uso del comando Math,BitXor
Author=Homes32
Level=5

[Variables]

[Process]
Math,BitXor,%result%,13,7

// Resultado de salida
Message,"Bitwise XOR:#$x#$x00001101 (13)#$x00000111 (7)#$x--------------#$x00001010 (10)#$x#$xReturn: %result%"
```
