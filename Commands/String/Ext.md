# StrFormat,Ext

Devuelve la extensión de archivo de una ruta.

## Sintaxis

```pebakery
StrFormat,Ext,<FilePath>,<%DestVar%>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| FilePath | La ruta completa del archivo. Esto también puede ser una URL. |
| DestVar | Variable donde se almacenará el resultado. |

## Observaciones

Si `FilePath` no existe, la operación fallará.

## Relacionado

[StrFormat,DirPath](./DirPath.md), [StrFormat,FileName](./FileName.md)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=StrFormat-Ext
Description=Mostrar el uso del comando StrFormat,Ext
Author=Homes32
Level=5
Version=1

[Variables]
%File%=C:\Windows\System32\HAL.DLL

[Process]
StrFormat,Ext,%File%,%result%
Message,"Extensión de archivo: %result%"
```
