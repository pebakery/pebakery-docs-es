# StrFormat,FileName

Devuelve la parte del nombre de archivo de una ruta.

## Sintaxis

```pebakery
StrFormat,FileName,<FilePath>,<%DestVar%>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| FilePath | La ruta completa del archivo. Esto también puede ser una URL. |
| DestVar | Variable donde se almacenará el resultado. |

## Observaciones

Si `FilePath` no existe, la operación fallará.

## Relacionado

[StrFormat,DirPath](./DirPath.md), [StrFormat,Ext](./Ext.md)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=StrFormat-FileName
Description=Mostrar el uso del comando StrFormat,FileName
Author=Homes32
Level=5
Version=1

[Variables]
%File%=C:\Windows\System32\HAL.DLL

[Process]
StrFormat,FileName,%File%,%result%
Message,"Nombre de archivo: %result%"
```

### Ejemplo 2

Recupere el nombre de archivo y la ruta de una URL.

```pebakery
[Main]
Title=StrFormat-FileName2
Description=Mostrar el uso del comando StrFormat,FileName
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
