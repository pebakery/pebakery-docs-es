# WimInfo

Recupera información sobre un archivo de imágenes de Windows (.wim).

## Sintaxis

```pebakery
WimInfo,<SrcWim>,<ImageIndex>,<Property>,<%DestVar%>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| SrcWim | La ruta completa a los archivos de origen que se capturarán. |
| ImageIndex | El índice de la imagen dentro del archivo .wim para recuperar información de. |
|| 0 - Recuperar información básica sobre el archivo WIM. Ver **Propiedades del archivo WIM**. |
|| 1 - Recupere información sobre la primera imagen en el archivo WIM. Ver **Propiedades de la imagen**. |
|| _n_ - Recuperar información sobre la imagen _n_ en el archivo WIM. |
| Property | La propiedad para consultar a partir de los datos XML de la imagen. Use el caracter `/` para acceder a las propiedades anidadas. Se puede acceder a múltiples propiedades anidadas mediante corchetes. (Ex. _WINDOWS/LANGUAGES/LANGUAGE[2]_ indica el segundo elemento _LANGUAGE_ anidado dentro del elemento _WINDOWS/LANGUAGES_). |
| DestVar | La variable donde se almacenará el valor de la `Property` especificada. |

### Propiedades del archivo WIM

Las siguientes propiedades se pueden recuperar desde el encabezado del archivo WIM.

| Propiedad | Descripción |
| --- | --- |
| ImageCount | La cantidad de imágenes que contiene el archivo WIM. |
| BootIndex | El índice de la imagen de arranque en el archivo .wim. Si no hay imágenes de arranque disponibles, el valor será cero. |
| Compression | El formato de compresión utilizado por el archivo WIM. `NINGUNO` `XPRESS` `LZX` `LZMS`. |

### Propiedades de la imagen

Las propiedades individuales de cada imagen se almacenan como datos XML dentro del archivo .wim. Estas propiedades incluyen información básica como el nombre de la imagen, descripción de la imagen, tamaño, conteo de archivos/directorios y marcas de tiempo creadas/modificadas. El formato XML también permite que se definan propiedades adicionales para cada imagen. Muchas veces esto es utilizado por el autor para incluir información que puede usarse para tomar una decisión sobre qué imagen debe seleccionarse, como la versión del producto, el idioma, la edición y la arquitectura del procesador.

#### Propiedades de imagen predeterminadas

Las siguientes propiedades específicas de la imagen se pueden recuperar:

| Propiedad | Descripción |
| --- | --- |
| DIRCOUNT | Número de directorios en la imagen. |
| FILECOUNT | Número de archivos en la imagen.  |
| TOTALBYTES | Número de archivos en la imagen. |
| HARDLINKBYTES | Espacio adicional que la imagen requerirá cuando se extraiga sin usar enlaces físicos. |
| CREATIONTIME | Contiene 2 propiedades: `HIGHTPART` y` LOWPART` que cuando se combinan como un entero de 64 bits representan una marca de tiempo de Windows. |
| CREATIONTIME/HIGHPART | Fecha de creación (Hex) |
| CREATIONTIME/LOWPART | Hora de creación (Hex) |
| LASTMODIFICATIONTIME | Contiene 2 propiedades: `HIGHTPART` y` LOWPART` que cuando se combinan como un entero de 64 bits representan una marca de tiempo de Windows. |
| LASTMODIFICATIONTIME/HIGHPART | Fecha modificada (Hex) |
| LASTMODIFICATIONTIME/LOWPART | Hora modificado (Hex) |
| NAME | Nombre de imagen definido por el usuario. |
| DESCRIPTION | Descripción de imagen definida por el usuario.  |
| FLAGS | Indicadores de imagen definidos por el usuario. |

#### Propiedades de imagen adicionales

Los datos XML del archivo WIM también pueden contener propiedades arbitrarias definidas por su autor.
La siguiente es una lista no exhaustiva de propiedades de imagen personalizadas utilizadas por las fuentes del sistema operativo Microsoft Windows.

| Propiedad | Descripción |
| --- | --- |
| DISPLAY NAME | Nombre "amistoso" utilizado por el instalador de Windows. |
| DISPLAYDESCRIPTION | Descripción "amigable" utilizada por el instalador de Windows. |
| INSTALLATIONTYPE | Tipo de instalación (Cliente/Servidor/Windows PE). |
| WINDOWS/VERSION/BUILD | Número de compilación de SO. |
| WINDOWS/VERSION/MAJOR | Versión principal del sistema operativo. |
| WINDOWS/VERSION/MINOR | Versión menor del sistema operativo. |
| WINDOWS/VERSION/SPBUILD | Número de compilación del Service Pack del sistema operativo. |
| WINDOWS/VERSION/SPLEVEL | Nivel de paquete de servicio del sistema operativo. |
| WINDOWS/LANGUAGES/DEFAULT | Idioma predeterminado del sistema operativo  |
| WINDOWS/EDITIONID | Edición de sistema operativo (Home/Professional) |

## Observaciones

WIMs divididos: PEBakery no admite la recuperación de información de archivos WIM divididos (.swm).

Este comando usa la [biblioteca de imágenes de Windows de código abierto (wimlib)](https://wimlib.net/).

## Relacionado

[WimMount](./WimMount.md), [WimUnmount](./WimUnmount.md), [WimCapture](./WimCapture.md), [WimAppend](./WimAppend.md), [WimApply](./WimApply.md), [WimExtract](./WimExtract.md), [WimExtractList](./WimExtractList.md)

## Ejemplos

### Ejemplo 1

Este script de ejemplo mostrará información sobre todas las imágenes en un archivo WIM.

```pebakery
[Main]
Title=WimInfo Ejemplo
Description=Demostrar recuperar información sobre un WIM y las imágenes que contiene.
Level=5
Version=1
Author=Homes32

[variables]
%wim%=C:\Temp\Win7\SOURCES\INSTALL.WIM

[Process]
// Obtenga la cantidad de imágenes en el archivo wim.
// El índice 0 hace referencia a los atributos del archivo WIM.
WimInfo,%wim%,0,ImageCount,%imgCount%
// Pasa por cada imagen y visualiza la información.
LOOP,%ScriptFile%,DisplayInfo,1,%imgCount%

[DisplayInfo]
System,SetLocal
WimInfo,%wim%,#c,WINDOWS/VERSION/MAJOR,%verMaj%
WimInfo,%wim%,#c,WINDOWS/VERSION/MINOR,%verMin%
WimInfo,%wim%,#c,WINDOWS/VERSION/BUILD,%verBld%
WimInfo,%wim%,#c,WINDOWS/VERSION/SPLEVEL,%verSP%
WimInfo,%wim%,#c,WINDOWS/LANGUAGES/LANGUAGE,%lang%
WimInfo,%wim%,#c,NAME,%imgName%
WimInfo,%wim%,#c,DESCRIPTION,%imgDescr%
WimInfo,%wim%,#c,FLAGS,%imgFlags%
WimInfo,%wim%,#c,DISPLAYNAME,%imgDispName%
WimInfo,%wim%,#c,DISPLAYDESCRIPTION,%imgDispDescr%
Message,"Imagen: #c de %imgCount%#$xVersion: %verMaj%.%verMin% (Build %verBld% Service Pack %verSP%)#$xLenguaje: %lang%#$xNombre: %imgName%#$xDescripción: %imgDescr%#$xFlags: %imgFlags%#$xNombre para mostrar: %imgDispName%#$xDescripción para mostrar: %imgDispDescr%"
System,EndLocal
```
