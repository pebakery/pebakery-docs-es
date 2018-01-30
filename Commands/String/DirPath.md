# StrFormat,DirPath

**Alias**: `StrFormat,Path`

Devuelve una ruta sin el nombre de archivo o extensión.

## Sintaxis

```pebakery
StrFormat,DirPath,<FilePath>,<%DestVar%>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| FilePath | La ruta completa del archivo. Esto también puede ser una URL. |
| DestVar | Variable donde se almacenará el resultado. |

## Observaciones

Si `FilePath` no existe, la operación fallará.

## Relacionado

[StrFormat,Ext](./Ext.md), [StrFormat,FileName](./FileName.md)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=StrFormat-DirPath
Description=Mostrar el uso del comando StrFormat,DirPath
Author=Homes32
Level=5
Version=1

[Variables]
%File%=C:\Windows\System32\HAL.DLL

[Process]
StrFormat,DirPath,%File%,%result%
Message,"DirPath: %result%"
```

### Ejemplo 2

Recuperar el nombre de archivo y la ruta de una URL.

```pebakery
[Main]
Title=StrFormat-DirPath2
Description=Mostrar el uso del comando StrFormat,DirPath
Author=Homes32
Level=5
Version=1

[Variables]
%URL%=http://live.sysinternals.com/Bginfo.exe

[Process]
StrFormat,FileName,%URL%,%name%
StrFormat,DirPath,%URL%,%path%
Message,"Descargando %name% desde#$x%path%"
```
