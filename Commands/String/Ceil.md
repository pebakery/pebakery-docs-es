# StrFormat,Ceil

Redondea un valor hacia arriba hasta el siguiente "tamaño" formateado (KB/MB/GB/TB/PB).

## Sintaxis

```pebakery
StrFormat,Ceil,<%Integer%>,<CeilTo>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| Integer | Variable que contiene el número para redondear hacia arriba. |
| CeilTo | Tamaño para redondear hacia arriba hasta. Puede ser uno de los siguientes: |
|| <Integer> - Un número entero positivo que representa el número de bytes de Ceil. |
|| K - Redondear hacia arriba hasta el próximo Kilobyte |
|| M - Redondear hacia arriba hasta el próximo Megabyte |
|| G - Redondear hacia arriba hasta el próximo Gigabyte |
|| T - Redondear hacia arriba hasta el próximo Terabyte |
|| P - Redondear hacia arriba hasta el próximo Petabyte |

## Observaciones

La variable `Integer` se sobrescribe con el resultado de la operación `StrFormat, Ceil`.

Este comando se puede usar junto con `StrFormat,IntToBytes` para regresar al tamaño legible para humanos redondeado al techo especificado.

Para las operaciones matemáticas de Techo usa el comando `Math,Ceil`.

## Relacionado

[Math,Ceil](../Math/Ceil.md), [Math,Floor](../Math/Floor.md), [Math,Round](../Math/Round.md), [StrFormat,Floor](./Floor.md), [StrFormat,IntToBytes](./IntToBytes.md), [StrFormat,Round](./Round.md)

## Ejemplos

### Ejemplo 1

En este ejemplo obtenemos el tamaño de un directorio en bytes, luego usamos `StrFormat,Ceil` para redondear al próximo Gigabyte y finalmente formateamos nuestro resultado con `StrFormat,IntToBytes`.

```pebakery
[Main]
Title=StrFormat-Ceil
Description=Mostrar el uso de StrFormat,Ceil.
Level=5
Version=1
Author=Homes32

[Variables]
%Dir%=C:\Windows\System32

[process]
DirSize,%Dir%,%Bytes%
// Veamos cuál es nuestro tamaño formateado antes de redondear
StrFormat,IntToBytes,%Bytes%,%StrSize%
// Redondear Bytes hasta el siguiente Gigabyte
StrFormat,Ceil,%Bytes%,g
// Use StrFormat para convertir el tamaño a un formato mas humanamente legible.
StrFormat,IntToBytes,%Bytes%,%StrCeilSize%
Message,"Bytes: [%Bytes%]#$xFormatted: [%StrSize%]#$xCeil: [%StrCeilSize%]"
```
