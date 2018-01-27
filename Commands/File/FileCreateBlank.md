# FileCreateBlank (Crear archivo en blanco)

Crear un archivo vacío.

## Sintaxis

```pebakery
FileCreateBlank,<FilePath>,[Encoding],[PRESERVE],[NOWARN]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| FilePath | Ruta para crear un archivo vacío. |
| Encoding | **(Opcional)** Codificación de caracteres para usar en el nuevo archivo. Codificaciones soportadas son : `UTF8`, `UTF16`, `UTF16BE`, `ANSI`. **por defecto** es `ANSI`. |

### Flags (Indicadores)

Los indicadores se pueden especificar en cualquier orden.

| Flag | Descripción |
| --- | --- |
| PRESERVE | **(Opcional)** No sobrescribir los archivos existentes. |
| NOWARN | **(Opcional)** No registrar una advertencia si el archivo se sobrescribe. |

## Observaciones

Algunos comandos como `TXTAddLine` requieren que el archivo exista antes de que pueda escribirse. Este comando puede ser para crear un archivo de texto vacío si el archivo de destino no existe.

Para archivos por lotes (*.bat, *.cmd), usar codificación `ANSI`. Para archivos de texto normal, la codificación `UTF16` o `UTF8` es muy recomendable.

## Relacionado

[TXTAddLine](../TXT/TXTAddLine.md)

## Ejemplos

### Ejemplo 1

Crear el archivo vacío Unicode.txt, escriba BOM (U + FEFF) codificado con UTF-16 Little Endian.

```pebakery
FileCreateBlank,C:\Temp\Unicode.txt,UTF16
```

### Ejemplo 2

Este script de muestra comprueba si el archivo de destino existe y usa `FileCreateBlank` para crearlo si es necesario.

```pebakery
[Main]
Title=FileCreateBlank (Crear archivo en blanco)
Description=Mostrar el uso de FileCreateBlank.
Level=5
Version=1
Author=Homes32

[Variables]
%grubMenu%=C:\Temp\menu.lst

[process]
If,Not,ExistFile,%grubMenu%,FileCreateBlank,%grubMenu%
TXTAddLine,%grubMenu%,"TÍTULO Menú principal",APPEND
```
