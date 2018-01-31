# StrFormat,IntToBytes

**Alias**: `StrFormat,Bytes`

Convierte una cantidad de bytes a un formato más humanamente legible.

Cualquier cantidad de bytes especificada se convertirá en una cadena que represente el tamaño en KB, MB, GB, TB or PB.

## Sintaxis

```pebakery
StrFormat,IntToBytes,<Bytes>,<%DestVar%>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| Bytes | Bytes a formatear. |
| DestVar | Variable donde se almacenará la cadena resultante. |

## Observaciones

Los comandos PEBakery como `DirSize`,`FileSize` y `System,GetFreeSpace` devuelven el tamaño en bytes. Esta función es útil para convertir el tamaño en bytes a un formato más legible para humanos.

La operación se puede revertir usando el comando `StrFormat,BytesToInt`.

## Relacionado

[DirSize](../File/DirSize.md), [FileSize](../File/FileSize.md), [StrFormat, BytesToInt](./BytesToInt), [System,GetFreeSpace](../System/GetFreeSpace.md)

## Ejemplos

### Ejemplo 1

En este ejemplo obtenemos el tamaño de un directorio usando `DirSize` y convertimos el resultado a un formato más legible.

```pebakery
[Main]
Title=IntToBytes
Description=Mostrar el uso del comando StrFormat,IntToBytes.
Level=5
Version=1
Author=Homes32

[Variables]
%Dir%=C:\Windows\System32

[process]
DirSize,%Dir%,%Size%
// Use StrFormat para convertir el tamaño a un formato más legible por humanos.
StrFormat,IntToBytes,%Size%,%StrSize%
Message,"Dir Size: %Size% bytes (%StrSize%)"
```
