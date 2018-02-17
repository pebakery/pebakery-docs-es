# WimApply

Extrae ("aplica") una imagen de un archivo de imágenes de Windows (.wim).

 Tenga en cuenta que `WimApply` está diseñado para extraer, o "aplicar", imágenes WIM enteras. Si desea extraer archivos o directorios específicos, utilice el comando `WimExtract` o `WimExtractBulk` en su lugar.

## Sintaxis

```pebakery
WimApply,<SrcWim>,<ImageIndex>,<DestDir>[,Split=<String>][,CHECK][,NOACL][,NOATTRIB]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| SrcWim | La ruta completa del archivo .wim que se extraerá. |
| ImageIndex | El índice de la imagen en el archivo .wim que se extraerá. |
| DestDir | La ruta completa al directorio donde se extraerá el archivo .wim. Se sobrescribirán todos los archivos duplicados existentes. Si la estructura del directorio no existe, se creará. |
| Split= | **(Opcional)** Una cadena que consiste en un archivo de estilo shell "GLOB" que especifica las partes adicionales del WIM dividido. El GLOB debe expandirse para incluir todas las partes del WIM dividido. Los comodines (? *) Son compatibles. |

### Flags (Indicadores)

Los siguientes indicadores se pueden usar de forma independiente y se pueden especificar en cualquier orden.

| Argumento | Descripción |
| --- | --- |
| CHECK | **(Opcional)** Verificar la integridad de `SrcWim` si contiene información de integridad adicional. |
| NOACL | **(Opcional)** No restaurar los descriptores de seguridad en los archivos y directorios extraídos. |
| NOATTRIB | **(Opcional)** No restaurar los atributos del archivo de Windows como de solo lectura, ocultos, etc.. |

## Observaciones

Integridad de los datos: para detectar daños accidentales (no maliciosos) en los datos, se calcula la suma de comprobación de cada archivo extraído y se devuelve un error si no coincide con la suma de comprobación incluida en el archivo WIM. Además, un archivo WIM puede incluir una tabla de integridad (sumas de comprobación adicionales) sobre los datos brutos de todo el archivo WIM. Por razones de rendimiento, PEBakery no verifica la tabla de integridad de manera predeterminada, pero se puede especificar el indicador `CHECK` para que lo haga.

Archivos ESD: PEBakery puede extraer archivos de WIM comprimidos sólidos o archivos "ESD" (.esd), al igual que los archivos WIM (.wim) normales.. Sin embargo, a veces Microsoft distribuye archivos ESD con segmentos cifrados; PEBakery no puede extraer dichos archivos hasta que no se hayan descifrado.
WIM divididos: PEBakery admite la extracción de archivos WIM divididos (.swm) usando el argumento `Split=`.

Este comando usa la [biblioteca de imágenes de Windows de código abierto (wimlib)](https://wimlib.net/).

## Relacionado

[WimMount](./WimMount.md), [WimUnmount](./WimUnmount.md), [WimExtract](./WimExtract.md), [WimExtractBulk](./WimExtractBulk.md)

## Ejemplos

### Ejemplo 1

Este ejemplo extraerá (aplicará) todo el contenido de la primera imagen de *C:\Temp\boot.wim* a una carpeta llamada *C:\Temp\Target*.

```pebakery
WimApply,C:\Temp\boot.wim,1,C:\Temp\Target
```

### Ejemplo 2

Este ejemplo extraerá (aplicará) todo el contenido de la primera imagen de un WIM dividido *C:\Temp\boot.swm* a una carpeta llamada *C:\Temp\Target*.

Para este ejemplo *C:\Temp\boot.swm* se divide en 5 partes:

```
C:\Temp\
|--- \boot.swm
|--- \boot2.swm
|--- \boot3.swm
|--- \boot4.swm
|--- \boot5.swm
```

```pebakery
WimApply,C:\Temp\boot.wim,1,C:\Temp\Target,Split="C:\Temp\boot*.swm"
```
