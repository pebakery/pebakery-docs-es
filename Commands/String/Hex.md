# StrFormat,Hex

Convierte un entero a su representación hexadecimal.

**Este comando se incluye para compatibilidad con Winbuilder 082. Se recomienda que actualice su código para usar el comando `Math,Hex`, más flexible..**

## Sintaxis

```pebakery
StrFormat,Hex,<Integer>,<%DestVar%>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| Integer | Number to convert. |
| DestVar | Variable where the resulting Hex representation will be stored. |

## Observaciones

Conversión de entero negativo es soportada.

Por compatibilidad con Winbuilder, solo se admiten enteros de 32 bits.

## Relacionado

[Math,Hex](../Math/Hex.md)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=StrFormat-Hex
Description=Mostrar el uso del comando StrFormat,Hex.
Level=5
Version=1
Author=Homes32

[Variables]
%Int1%=88888888
%Int2%=-2

[process]
StrFormat,Hex,%Int1%,%result1%
StrFormat,Hex,%Int2%,%result2%
Message,"Entrada: [%Int1%] Hex: [0x%result1%]#$xEntrada: [%Int2%] Hex: [0x%result2%]"
```
