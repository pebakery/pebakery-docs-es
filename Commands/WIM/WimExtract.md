# WimExtract

Extrae uno o más archivos o árboles de directorios de un archivo de imagen de Windows (.wim).

Se admiten comodines, lo que permite copiar múltiples archivos o directorios a la vez.

Tenga en cuenta que `WimExtract` está destinado a extraer solo un subconjunto de una imagen WIM. Si desea extraer o "aplicar" una imagen WIM completa, use el comando `WimApply` en su lugar.

## Sintaxis

```pebakery
WimExtract,<SrcWim>,<ImageIndex>,<ExtractPath>,<DestDir>[,Split=<String>][,CHECK][,NOACL][,NOATTRIB]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| SrcWim | La ruta completa del archivo .wim para extraer archivos de. |
| ImageIndex | El índice de la imagen dentro del archivo .wim que contiene los archivos que se extraerán. |
| ExtractPath | La ruta completa del archivo(s) dentro de la imagen que se extraerá. Los comodines (* ?) Están permitidos. |
| DestDir | La ruta completa al directorio donde se extraerán los archivos. Se sobrescribirán todos los archivos duplicados existentes. Si la estructura del directorio no existe, se creará. |
| Split= | **(Opcional)** Una cadena que consiste en un archivo de estilo shell "GLOB" que especifica las partes adicionales del WIM dividido. El GLOB debe expandirse para incluir todas las partes del WIM dividido. Los comodines (? *) Son compatibles. |

### Flags (Indicadores)

Los siguientes indicadores se pueden usar de forma independiente y se pueden especificar en cualquier orden.

| Argumento | Descripción |
| --- | --- |
| CHECK | **(Opcional)** Verifique la integridad de `SrcWim` si contiene información de integridad adicional. |
| NOACL | **(Opcional)** No restaure los descriptores de seguridad en los archivos y directorios extraídos. |
| NOATTRIB | **(Opcional)** No restaure los atributos del archivo de Windows como de solo lectura, ocultos, etc.. |

## Observaciones

Integridad de los datos: para detectar daños accidentales (no maliciosos) en los datos, se calcula la suma de comprobación de cada archivo extraído y se devuelve un error si no coincide con la suma de comprobación incluida en el archivo WIM. Además, un archivo WIM puede incluir una tabla de integridad (sumas de comprobación adicionales) sobre los datos brutos de todo el archivo WIM. Por razones de rendimiento, PEBakery no verifica la tabla de integridad de forma predeterminada, pero el indicador `CHECK` se puede especificar para que lo haga.

Archivos ESD: PEBakery puede extraer archivos de WIM comprimidos sólidos o archivos "ESD" (.esd), al igual que los archivos WIM (.wim) normales. Sin embargo, a veces Microsoft distribuye archivos ESD con segmentos cifrados; PEBakery no puede extraer dichos archivos hasta que no se hayan descifrado.

WIMs divididos: PEBakery admite la extracción de archivos WIM divididos (.swm) usando el argumento `Split=`.

Este comando usa la [biblioteca de imágenes de Windows de código abierto (wimlib)](https://wimlib.net/).

## Relacionado

[WimMount](./WimMount.md), [WimUnmount](./WimUnmount.md), [WimApply](./WimApply.md), [WimExtractBulk](./WimExtractBulk.md)

## Ejemplos

### Ejemplo 1

Este ejemplo extrae un solo archivo de la primera imagen de *C:\Temp\boot.wim* a una carpeta llamada *C:\Temp\Target*.

```pebakery
Echo,"Extrayendo Regedit..."
WimExtract,C:\Temp\boot.wim,1,Windows\regedit.exe,C:\Temp\Target
```

### Ejemplo 2

Este ejemplo extraerá todos los archivos .dll del directorio *Windows\System32* en la primera imagen de *C:\Temp\boot.wim* to a folder called *C:\Temp\Target*. Security Descriptors will not be retained.

```pebakery
Echo,"Extrayendo todos los archivos dll de [boot.wim] [Index: 1] a Windows\System32..."
WimExtract,C:\Temp\boot.wim,1,Windows\System32\*.dll,C:\Temp\Target,NOACL
```
