# WimUnmount

Desmonta una imagen montada de un archivo de imágenes de Windows (.WIM) desde el directorio especificado.

## Sintaxis

```pebakery
WimMount,<MountDir>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| MountDir | La ruta completa al directorio donde está montado el archivo .wim. Si el directorio no existe o no hay una imagen montada, la operación fallará. |

## Observaciones

Este comando usa la biblioteca `wimgapi.dll` incluida con Microsoft Windows.

## Relacionado

[WimMount](./WimMount.md)

## Ejemplos

Desmonta la imagen de install.wim montada en nuestra carpeta *%BaseDir%\Mount\InstallWim*.

### Ejemplo 1

```pebakery
[Main]
Title=WimUnmount Ejemplo
Description=Mostrar el uso del comando WimUnmount.
Author=Homes32
Level=5
Version=1

[Variables]
%InstallWim%=C:\W10\x64\sources\install.wim
%WimIndex%=4
%MountDir%=C:\PEBakery\Mount\Win10PESE\Source\InstallWimSrc

[Process]
// El directorio %MountDir% debe existir o la operación de montaje fallará.
If,Not,EXISTDIR,%MountDir%,DirMake,%MountDir%
Echo,"MountingMontando Install.wim from#$x--> %InstallWim% [Index: %WimIndex%]"
// Montar la imagen con índice 4
WimMount,%InstallWim%,%WimIndex%,%MountDir%
Echo,"Aquí es donde copiarías algunos archivos, etc..."
Wait,10
// Limpieza después de nosotros mismos...
Echo,"Desmontando %MountDir%..."
WimUnmount,%MountDir%
```
