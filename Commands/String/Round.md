# StrFormat,Round

Redondea un valor al "tamaño" formateado más cercano (KB/MB/GB/TB/PB).

## Sintaxis

```pebakery
StrFormat,Round,<%Integer%>,<RoundTo>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| Integer | Variable que contiene el número a redondear. |
| FloorTo | Tamaño para redondear. Puede ser uno de los siguientes: |
|| <Integer> - Un entero positivo que representa la cantidad de bytes a redondear a. |
|| K - Redondear a Kilobyte |
|| M - Redondear a Megabyte |
|| G - Redondear a Gigabyte |
|| T - Redondear a Terabyte |
|| P - Redondear a Petabyte |

## Observaciones

La variable `Integer` se sobrescribe con el resultado de la operación `StrFormat, Round`.
Este comando se puede usar junto con `StrFormat,IntToBytes` para regresar al tamaño legible para humanos redondeado al entero más cercano.

Para operaciones de redondeo matemático use el comando `Math, Round`.

## Relacionado

[Math,Ceil](../Math/Ceil.md), [Math,Floor](../Math/Floor.md), [Math,Round](../Math/Round.md), [StrFormat,Ceil](./Ceil.md), [StrFormat,Floor](./Floor.md), [StrFormat,IntToBytes](./IntToBytes.md)

## Ejemplos

### Ejemplo 1

En este ejemplo obtenemos el tamaño de un directorio en bytes, luego usamos `StrFormat,Floor` para redondear al Gigabyte más cercano y finalmente formateamos nuestro resultado con `StrFormat,IntToBytes`.
```pebakery
[Main]
Title=StrFormat-Round
Description=Mostrar el uso del comando StrFormat,Round.
Level=5
Version=1
Author=Homes32

[Variables]
%Dir%=C:\Windows\System32

[process]
DirSize,%Dir%,%Bytes%
// Veamos cuál es nuestro tamaño formateado antes de redondear
StrFormat,IntToBytes,%Bytes%,%StrSize%
// Bytes redondeados al Gigabyte más cercano
StrFormat,Round,%Bytes%,g
// Use StrFormat para convertir el tamaño a un formato más legible para humanos.
StrFormat,IntToBytes,%Bytes%,%StrFloorSize%
Message,"Bytes: [%Bytes%]#$xFormateado: [%StrSize%]#$xRedondeo: [%StrFloorSize%]"
```
