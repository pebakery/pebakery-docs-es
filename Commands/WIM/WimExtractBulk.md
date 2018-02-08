# WimExtractBulk

Utiliza un "archivo de lista" para extraer uno o más archivos o árboles de directorios de un archivo de imágenes de Windows (.wim).

Se admiten comodines, lo que permite copiar múltiples archivos o directorios a la vez.

Note that `WimExtractBulk` is intended for extracting only a subset of a WIM image. If you want to extract or "apply" a full WIM image use the `WimApply` command instead.

## Sintaxis

```pebakery
WimExtractBulk,<SrcWim>,<ImageIndex>,<DestDir>,<ListFile>[,Split=<String>][,CHECK][,NOACL][,NOATTRIB]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| SrcWim | La ruta completa del archivo .wim para extraer archivos de. |
| ImageIndex | El índice de la imagen dentro del archivo .wim que contiene los archivos que se extraerán. |
| DestDir | La ruta completa al directorio donde se extraerán los archivos. Se sobrescribirán todos los archivos duplicados existentes. Si la estructura del directorio no existe, se creará. |
| ListFile | La ruta completa es un archivo de texto que contiene una lista de rutas para extraer. Consulte la _Especificación de archivo de lista_ más abajo para más detalles. |
| Split= | Una cadena que consiste en un archivo de estilo shell "GLOB" que especifica las partes adicionales del WIM dividido. El GLOB debe expandirse para incluir todas las partes del WIM dividido. Los comodines (? *) Son compatibles. |

### Flags (Indicadores)

Los siguientes indicadores se pueden usar de forma independiente y se pueden especificar en cualquier orden.

| Argumento | Descripción |
| --- | --- |
| CHECK | **(Opcional)** Verifique la integridad de `SrcWim` si contiene información de integridad adicional. |
| NOACL | **(Opcional)** No restaure los descriptores de seguridad en los archivos y directorios extraídos. |
| NOATTRIB | **(Opcional)** No restaure los atributos del archivo de Windows como de solo lectura, ocultos, etc.. |

### Especificación de archivo de lista

Los archivos de lista son archivos de texto que contienen una lista de rutas para extraer de la imagen WIM.

Los archivos de lista deben obedecer las siguientes reglas:

- Solo se permite una ruta por línea.
- Todas las rutas son relativas al directorio raíz de la imagen.
- Las rutas no son sensibles a mayúsculas y minúsculas.
- Los comodines (*,?) Están permitidos y pueden expandirse para incluir múltiples archivos o directorios.
- Ambos caracteres fowardslash `/` y backslash `\` son compatibles. El `\` principal es opcional.
- Los comentarios deben estar en su propia línea y comenzar con `;` o `#`.
- No es necesario citar caminos que contengan espacios. (ejem. _\Program Files\Common Files_)
- El espacio en blanco se ignora.

Nota: PEBakey convierte internamente el archivo de lista para usar la codificación `UTF-16LE`.

#### Ejemplo de archivo de lista

```pebakery
; Este es un comentario
# Esto también es un comentario
\Users
\Windows\explorer.exe
Windows\System32\en-US\*

; No es necesario citar rutas que contengan espacios internos.
/Program Files/M*

; Se ignora el espacio en blanco inicial y final

   \Windows\notepad*

```

## Observaciones

Integridad de los datos: para detectar daños accidentales (no maliciosos) en los datos, se calcula la suma de comprobación de cada archivo extraído y se devuelve un error si no coincide con la suma de comprobación incluida en el archivo WIM. Además, un archivo WIM puede incluir una tabla de integridad (sumas de comprobación adicionales) sobre los datos brutos de todo el archivo WIM. Por razones de rendimiento, PEBakery no verifica la tabla de integridad de manera predeterminada, pero se puede especificar el indicador `CHECK` para que lo haga.

Archivos ESD: PEBakery puede extraer archivos de WIM comprimidos sólidos o archivos "ESD" (.esd), al igual que los archivos WIM (.wim) normales. Sin embargo, a veces Microsoft distribuye archivos ESD con segmentos cifrados; PEBakery no puede extraer dichos archivos hasta que no se hayan descifrado.

WIMs divididos: PEBakery admite la extracción de archivos divididos WIM (.swm) usando el argumento `Split=`.

Este comando usa la [biblioteca de imágenes de Windows de código abierto (wimlib)](https://wimlib.net/).

## Relacionado

[WimMount](./WimMount.md), [WimUnmount](./WimUnmount.md), [WimApply](./WimApply.md), [WimExtract](./WimExtract.md)

## Ejemplos

### Ejemplo 1

Este ejemplo extrae varios archivos y directorios de la 4ª imagen de *C:\Temp\install.wim* a una carpeta llamada *C:\Temp\Target* usando un `ListFile` llamado *FileList.txt*.

```pebakery
Echo,"Extrayendo de ListFile..."
WimExtractBulk,%install.wim%,4,C:\Temp\Target\Extract,C:\Temp\Target\FileList.txt,NOACL
```

FileList.txt

```pebakery
; Directorios
Windows\Fonts\
Program Files\
Windows\Globalization\
Windows\??-??\
Windows\system32\en-US\
Program Files\
ProgramData\
users\
Windows\inf\
Windows\winsxs\*_microsoft-windows-servicingstack*\
Windows\servicing\
Windows\system32\boot\
Windows\system32\Dism\
Windows\system32\driverstore\
Windows\system32\drivers\
Windows\system32\wbem\
Windows\system32\Recovery\
Windows\system32\SMI\

Windows\winsxs\*_microsoft.windows.c..-controls.resources*\
Windows\winsxs\*_microsoft.windows.common-controls*\
Windows\winsxs\*_microsoft.windows.gdiplus*\
Windows\winsxs\*_microsoft.windows.isolationautomation*\
Windows\Globalization\

; Archivos
Windows\*.*

Windows\Boot\PXE\??-??\bootmgr.exe.mui
Windows\Boot\EFI\bootmgfw.efi
Windows\system32\config\components
Windows\system32\config\Default
Windows\system32\config\sam
Windows\system32\config\Security
Windows\system32\config\software
Windows\system32\config\system
Windows\winsxs\manifests\*_microsoft.windows.c..-controls.resources*
Windows\winsxs\manifests\*_microsoft.windows.common-controls*
Windows\winsxs\manifests\*_microsoft.windows.gdiplus*
Windows\winsxs\manifests\*_microsoft.windows.isolationautomation*
Windows\winsxs\manifests\*_microsoft.windows.systemcompatible*
Windows\winsxs\manifests\*_microsoft.windows.i..utomation.proxystub*
Windows\system32\api-ms-*.dll
Windows\system32\*.dat
Windows\system32\*.exe
Windows\system32\??-??\*.exe.mui
Windows\system32\??-??\*.ocx.mui
Windows\WindowsShell.Manifest
Windows\system32\*.ocx
Windows\system32\*.com
Windows\system32\*.cmd
Windows\system32\hal*.dll
Windows\system32\KBDUS.DLL
Windows\system32\KBD*.DLL
```
