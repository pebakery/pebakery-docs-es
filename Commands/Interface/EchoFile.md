# EchoFile

Escribe el contenido de un archivo en el registro.

## Sintaxis

```pebakery
EchoFile,<SrcFile>[,WARN][,ENCODE]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| SrcFile | La ruta completa del archivo para escribir en el registro. |

### Flags (Indicadores)

Los indicadores son opcionales y pueden especificarse en cualquier orden.

| Flag | Descripción |
| --- | --- |
| WARN | Marca el `Mensaje` como una advertencia en el registro. |
| ENCODE | Incruste el archivo en el registro utilizando la función `Encode` de PEBakery. |

## Observaciones

`EchoFile` está diseñado para ser utilizado por los desarrolladores con el fin de recopilar registros adicionales, archivos de configuración, etc. para ayudar en la resolución de problemas. El indicador `ENCODE` se puede usar para adjuntar archivos que no son de texto que se pueden extraer con el comando` Extract` de PEBakery.

## Relacionado

[Echo](./Echo.md), [Message](./Message.md)

## Ejemplos

### Ejemplo 1

```pebakery
[main]
Title=EchoFile Ejemplo
Description=Mostrar el uso del comando EchoFile.
Level=5
Version=1
Author=Homes32

[variables]
%LogFile%=%BaseDir%\Temp\myLog.txt

[process]
// Crear un archivo de registro ficticio.
FileCreateBlank,%LogFile%
TXTAddLine,%LogFile%,Line1,Append
TXTAddLine,%LogFile%,Line2,Append
TXTAddLine,%LogFile%,Line3,Append
TXTAddLine,%LogFile%,Line4,Append
TXTAddLine,%LogFile%,Line5,Append

// EchoFile
EchoFile,%LogFile%

// EchoFile con ENCODE
EchoFile,%LogFile%,ENCODE
```
