# FileSize (Tamaño del archivo)

**Alias**: `Retrieve,FileSize`

Obtiene el tamaño de un archivo.

## Sintaxis

```pebakery
FileSize,<FilePath>,<DestVar>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| FilePath | Ruta completa del archivo. |
| DestVar | Variable donde se almacenará el tamaño del archivo (en bytes). |

## Observaciones

Puede usar `StrFormat,Bytes` para convertir el tamaño a un formato mas humanamente legible. (Ej. 3.5MB)

## Relacionado

[DirSize](./DirSize), [StrFormat,Bytes](../String/Bytes.md)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=FileSize (Tamaño del archivo)
Description=Mostrar el uso de FileSize.
Level=5
Version=1
Author=Homes32

[Variables]
%File%=C:\Windows\notepad.exe

[process]
FileSize,%File%,%Size%
// Usar `StrFormat,Bytes` para convertir el tamaño a un formato mas humanamente legible.
StrFormat,Bytes,%Size%,%StrSize%
Message,"Tamaño del archivo: %Size% bytes (%StrSize%)"
```
