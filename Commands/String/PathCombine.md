# StrFormat,PathCombine

Combina una ruta con un nombre de archivo para formar una ruta completa.

## Sintaxis

```pebakery
StrFormat,PathCombine,<DirPath>,<FileName>,<%DestVar%>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| DirPath | La ruta del archivo. |
| FileName | El nombre y la extensión del archivo. |
| DestVar | Variable donde se almacenará el resultado. |

## Observaciones

PEBakery añadirá un `\` a `DirPath` si no existe.

## Relacionado

[StrFormat,DirPath](./DirPath.md), [StrFormat,Ext](./Ext.md), [StrFormat,FileName](./FileName.md)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=StrFormat-PathCombine
Description=Mostrar el uso del comando StrFormat,PathCombine
Author=Homes32
Level=5
Version=1

[Variables]
%File%=HAL.DLL
%Path%=C:\Windows\System32\

[Process]
StrFormat,PathCombine,%Path%,%File%,%result%
Message,"Ruta combinada: %result%"
```
