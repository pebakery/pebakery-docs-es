# DirSize (Tamaño del directorio)

**Alias**: `Retrieve,DirSize`

Obtiene el tamaño de un directorio.

## Sintaxis

```pebakery
DirSize,<DirPath>,<%DestVar%>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| DirPath | Ruta completa del directorio. |
| DestVar | Variable donde se almacenará el tamaño del directorio (en bytes). |

## Observaciones

Si `DirPath` contiene archivos a los que no se puede acceder con privilegios de `Administrator`, PEBakery los ignora.

Puede usar `StrFormat, Bytes` para convertir el tamaño a un formato más humanamente legible. (Ej. 3.5GB)

## Relacionado

[FileSize](./FileSize.md), [StrFormat,Bytes](../String/Bytes.md)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=DirSize (Tamaño del directorio)
Description=Mostrar el uso de DirSize.
Level=5
Version=1
Author=Homes32

[Variables]
%Dir%=C:\Windows\System32

[process]
DirSize,%Dir%,%Size%
// Usar StrFormat para convertir el tamaño a un formato más humanamente legible.
StrFormat,Bytes,%Size%,%StrSize%
Message,"Tamaño del directorio: %Size% bytes (%StrSize%)"
```
