# StrFormat,ShortPath

Convierte una ruta en formato compatible con `DOS 8.3`.

**Este comando ha quedado obsoleto y se eliminará en una versión futura.**

## Sintaxis

```pebakery
StrFormat,ShortPath,<Path>,<%DestVar%>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| Path | The full path to convert. |
| DestVar | The variable where the result will be saved. |

## Observaciones

La conversión exitosa a una ruta corta depende del valor de registro `HKLM\System\CurrentControlSet\Control\FileSystem\NtfsDisable8dot3NameCreation`, por lo que no se puede garantizar que este comando funcione correctamente en todos los sistemas.

## Relacionado

[StrFormat,LongPath](./LongPath.md)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=StrFormat-ShortPath Ejemplo
Description=Mostrar el uso del comando StrFormat,ShortPath.
Level=5
Version=1
Author=Homes32

[variables]
%path%="C:\Program Files (x86)\Notepad++\Notepad++.exe"

[process]
StrFormat,ShortPath,%path%,%result%
Message,"Ruta corta: %result%"
```
