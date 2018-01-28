# Math,Hex

Convierte un entero a su representación hexadecimal.

## Sintaxis

```pebakery
Math,Hex,<%DestVar%>,<Integer>[,BitSize]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| DestVar | La variable donde se almacenará el resultado. |
| Integer | El entero que se convertirá a hexadecimal. |
| Size | **(Opcional)** Tamaño del número en bits: `8` `16` `32` `64` |

## Observaciones

Conversión de entero negativo es compatible.

## Relacionado

[StrFormat,Hex](../String/Hex.md)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=Math-Hex Ejemplo
Description=Mostrar el uso del comando Math,Hex.
Level=5
Version=1
Author=Homes32

[Variables]

[process]
Math,Hex,%result1%,3735928559
Math,Hex,%result2%,88888888
Math,Hex,%result3%,2343432205
Math,Hex,%result4%,-2,64
Math,Hex,%result5%,-2,32

Message,"Entrada: [3735928559] Hex: [%result1%]#$x#$xInput: [88888888] Hex: [%result2%]#$x#$xInput: [2343432205] Hex: [%result3%]#$x#$xInput: [-2] Hex: [%result4%] (64bit)#$x#$xInput: [-2] Hex: [%result5%] (32bit)"
```
