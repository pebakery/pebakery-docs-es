# StrFormat,LongPath

Convierte una ruta `DOS 8.3` a una ruta larga `NT`.

**Este comando ha quedado obsoleto y se eliminará en una versión futura.**

## Sintaxis

```pebakery
StrFormat,LongPath,<Path>,<%DestVar%>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| Path | El camino completo a convertir. |
| DestVar | La variable donde se guardará el resultado. |

## Observaciones

La conversión exitosa a una ruta larga depende del valor de registro `HKLM\System\CurrentControlSet\Control\FileSystem\NtfsDisable8dot3NameCreation`, por lo tanto, no se puede garantizar que este comando funcione correctamente en todos los sistemas.

## Relacionado

[StrFormat,ShortPath](./ShortPath.md)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=StrFormat-LongPath Ejemplo
Description=Mostrar el uso del comando StrFormat,LongPath.
Level=5
Version=1
Author=Homes32

[variables]
%path%="C:\Progra~2\Notepad++\Notepad++.exe"

[process]
StrFormat,LongPath,%path%,%result%
Message,"LongPath: %result%"
```
