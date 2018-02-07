# WimMount

Monta una imagen desde un archivo de imágenes de Windows (.WIM) al directorio especificado.

## Sintaxis

```pebakery
WimMount,<ImageFile>,<Index>,<MountDir>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| ImageFile | La ruta completa al archivo .wim que se va a montar. |
| Index | El índice de la imagen en el archivo .wim que se va a montar. |
| MountDir | La ruta completa al directorio donde se va a montar el archivo .wim. Si el directorio no existe o ya hay una imagen montada, la operación fallará. |

## Observaciones

Debe desmontar la imagen con el comando `WimUnmount` cuando haya terminado.

Este comando usa la biblioteca `wimgapi.dll` incluida con Microsoft Windows.

## Relacionado

[WimUnmount](./WimUnmount.md)

## Ejemplos

Monte la imagen install.wim a nuestra carpeta *%BaseDir%\Mount\InstallWim*.

### Ejemplo 1

```pebakery
[Main]
Title=WimMount Ejemplo
Description=Mostrar el uso del comando WimMount.
Author=Homes32
Level=5
Version=1

[Variables]
%InstallWim%=C:\W10\x64\sources\install.wim
%WimIndex%=4
%MountDir%=C:\PEBakery\Mount\Win10PESE\Source\InstallWimSrc

[Process]
// el directorio %MountDir% debe existir o la operación de montaje fallará.
If,Not,EXISTDIR,%MountDir%,DirMake,%MountDir%
Echo,"Mounting Install.wim from#$x--> %InstallWim% [Index: %WimIndex%]"
// Montar la imagen con índice 4
WimMount,%InstallWim%,%WimIndex%,%MountDir%
Echo,"Aquí es donde copiarías algunos archivos, etc..."
Wait,10
// Limpieza después de nosotros mismos...
Echo,"Desmontando %MountDir%..."
WimUnmount,%MountDir%
```
