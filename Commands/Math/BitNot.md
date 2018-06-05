# Math,BitNot

Realiza una operación NO bit a bit.

## Sintaxis

```pebakery
Math,BitNot,<%DestVar%>,<Value>[,Size]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| DestVar | La variable donde se almacenará el resultado. |
| Value | El valor para operar en. |
| Size | **(Opcional)** Tamaño del `Value` en bits: `8` `16` `32` `64` |

## Observaciones

Default bit size is 32bit.

## Relacionado

[BitAnd](./BitAnd.md), [BitOr](./BitOr.md), [BitShift](./BitShift.md), [BitXor](./BitXor.md)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=Math-BitNot Ejemplo
Description=Mostrar el uso del comando Math,BitNot
Author=Homes32
Level=5

[Variables]

[Process]
Math,BitNot,%result%,106

// Resultado de salida
Message,"Bitwise NOT:#$x#$x00000000000000000000000001101010 (106)#$x11111111111111111111111110010101 (4294967189)#$x#$xReturn: %result%"
```
