# StrFormat,BytesToInt

Convierte una cadena legible por humanos que representa el tamaño de un archivo o directorio en un entero legible por máquina que representa el tamaño en bytes.

Las cadenas se pueden convertir a bytes desde KB, MB, GB, TB or PB.

## Sintaxis

```pebakery
StrFormat,BytesToInt,<String>,<%DestVar%>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| String | Cadena que contiene el tamaño formateado. |
| DestVar | Variable donde se almacenarán los bytes resultantes. |

## Observaciones

Esta operación puede usarse para invertir el comando `StrFormat,IntToBytes` y convertir los tamaños legibles para humanos en formato legible por máquina.

El espacio en blanco de la cadena se descarta, por lo que `5,123 GB` se trata de la misma manera que` 5,123 GB`.

## Relacionado

[DirSize](../File/DirSize.md), [FileSize](../File/FileSize.md), [StrFormat, IntToBytes](./IntToBytes), [System,GetFreeSpace](../System/GetFreeSpace.md)

## Ejemplos

### Ejemplo 1

En este ejemplo convertimos una cadena que contiene el tamaño `5.274GB` en bytes.

```pebakery
[Main]
Title=BytesToInt
Description=Mostrar el uso de StrFormat,BytesToInt.
Level=5
Version=1
Author=Homes32

[Variables]
%StrSize%="5.274GB"

[process]
// Use StrFormat para convertir el formato legible por humanos a un formato legible por máquina.
StrFormat,BytesToInt,%StrSize%,%Size%
Message,"Size: %StrSize% (%Size% bytes)"
```
