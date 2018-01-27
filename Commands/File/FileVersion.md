# FileVersion (Versión del archivo)

**Alias**: `Retrieve,FileVersion`

Recupera el número de versión del archivo especificado.

## Sintaxis

```pebakery
FileVersion,<FilePath>,<DestVar>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| FilePath | Ruta completa del archivo. |
| DestVar | Variable donde se almacenará la versión del archivo. |

## Observaciones

Si la información de la versión no está disponible, el comando regresa `0.0.0.0`

## Relacionado

## Ejemplo

```pebakery
[Main]
Title=FileVersion (Versión del archivo)
Description=Mostrar el uso de FileVersion.
Level=5
Version=1
Author=Homes32

[Variables]
%File%=C:\Windows\notepad.exe

[process]
FileVersion,%File%,%Ver%
Message,"%File%#$xVersión del archivo: %Ver%"
```
