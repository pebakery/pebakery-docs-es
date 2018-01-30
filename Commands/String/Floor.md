# StrFormat,Floor

Redondea un valor hacia abajo hasta el "tamaño" formateado (KB/MB/GB/TB/PB).

## Sintaxis

```pebakery
StrFormat,Floor,<%Integer%>,<FloorTo>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| Integer | Variable que contiene el número para redondear hacia abajo. |
| FloorTo | Tamaño para redondear hacia abajo. Puede ser uno de los siguientes: |
|| <Integer> - Un entero positivo que representa la cantidad de bytes para redondear hacia abajo. |
|| K - Redondea hacia abajo a Kilobyte |
|| M - Redondea hacia abajo a Megabyte |
|| G - Redondea hacia abajo a Gigabyte |
|| T - Redondea hacia abajo a Terabyte |
|| P - Redondea hacia abajo a Petabyte |

## Observaciones

La variable `Integer` se sobrescribe con el resultado de la operación `StrFormat,Floor`.

Este comando se puede usar junto con `StrFormat,IntToBytes` para regresar al tamaño legible para humanos redondeado al piso especificado.

Para operaciones matemáticas de redondeo hacia abajo usar el comando `Math,Floor`.

## Relacionado

[Math,Ceil](../Math/Ceil.md), [Math,Floor](../Math/Floor.md), [Math,Round](../Math/Round.md), [StrFormat,Ceil](./Ceil.md), [StrFormat,IntToBytes](./IntToBytes.md), [StrFormat,Round](./Round.md)

## Ejemplos

### Ejemplo 1

En este ejemplo obtenemos el tamaño de un directorio en bytes, luego usamos `StrFormat,Floor` para redondear al inferior Gigabyte y finalmente formateamos nuestro resultado con `StrFormat,IntToBytes`.

```pebakery
[Main]
Title=StrFormat-Floor
Description=Mostrar el uso del comando StrFormat,Floor.
Level=5
Version=1
Author=Homes32

[Variables]
%Dir%=C:\Windows\System32

[process]
DirSize,%Dir%,%Bytes%
// Veamos cuál es nuestro tamaño formateado antes de redondear
StrFormat,IntToBytes,%Bytes%,%StrSize%
// Redondear Bytes hasta el anterior Gigabyte
StrFormat,Floor,%Bytes%,g
// Use StrFormat para convertir el tamaño a un formato mas humanamente legible.
StrFormat,IntToBytes,%Bytes%,%StrFloorSize%
Message,"Bytes: [%Bytes%]#$xFormato: [%StrSize%]#$xPiso: [%StrFloorSize%]"
```
