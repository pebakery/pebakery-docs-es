# System,SaveLog

Exporta el archivo de registro actual..

## Sintaxis

```pebakery
System,SaveLog,<DestPath>[,Format]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| DestPath | La ruta completa donde se guardará el registro. Si el archivo existe, se sobrescribirá. |
| Format | Los registros se pueden exportar a los siguientes formatos: |
|| HTML - **(Por defecto)** Exporta el registro como un documento html que se puede ver fácilmente en un navegador web. |
|| Text - Exporta el registro como un archivo UTF8 .txt legible por máquina. |

## Observaciones

Ninguna.

## Relacionado

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=SaveLog Ejemplo
Author=Homes32
Description=Mostrar el uso del comando System,SaveLog.
Version=1
Level=5

[Interface]

[variables]

[process]
Echo,"Haciendo algunas cosas...."
FileCreateBlank,%BaseDir%\Temp\myFile.txt
FileDelete,%BaseDir%\Temp\myFile.txt
// Obtenga una marca de tiempo para nuestro nombre de archivo de registro para evitar sobrescrituras
StrFormat,DATE,%Timestamp%,"yyyy-mmm-dd-hhnn"
Echo,"Exportando el registro como [HTML]..."
System,SaveLog,%BaseDir%\%Timestamp%-myLog.html
Echo,"Exportando el registro como [Text]..."
System,SaveLog,%BaseDir%\%Timestamp%-myLog.txt,Text
Echo,"Hecho."
```
