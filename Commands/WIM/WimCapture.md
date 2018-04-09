# WimCapture

Crea un nuevo archivo de imágenes de Windows (.wim).

## Sintaxis

```pebakery
WimCapture,<SrcDir>,<DestWim>,<Compress>[,ImageName=<String>][,ImageDesc=<String>][,Flags=<String>][,BOOT][,CHECK][,NOACL]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| SrcWim | La ruta completa a los archivos de origen que se capturarán. |
| DestWim | La ruta completa al archivo .wim que se está creando. Si el archivo existe, se sobrescribirá. Si la estructura del directorio no existe, la operación fallará. |
| Compress | Niveles de compresión admitidos: |
|| NONE - Sin Compresión. |
|| XPRESS - Compresión y descompresión rápidas, pero da como resultado un tamaño de imagen más grande. _ (Similar a DISM.exe /compress: fast)_ |
|| LZX - Zip estilo DEFLATE compresión. _ (Similar a DISM.exe: /compress: maximum) _ |
|| LZMS - Formato de compresión no documentado de Microsoft similar al algoritmo LZMA utilizado por 7zip. Tamaño de imagen más pequeño, pero toma mucho más tiempo para comprimir. _ (Similar a DISM.exe /compress:recovery) _ |
| ImageName= | **(Opcional)** El nombre único para la imagen que se está capturando. Si no se especifica, se usará de forma predeterminada el componente de nombre de archivo de `SrcWim`. |
| ImageDesc= | **(Opcional)** Información adicional sobre la imagen. |
| Flags= | **(Opcional)** Especifique una cadena para usar en el elemento `<FLAGS>` de los datos XML para la nueva imagen. |

Los argumentos `ImageName =`, `ImageDesc =`, y `Flags =` se pueden usar de forma independiente y se pueden especificar en cualquier orden.

### Flags (Indicadores)

Los siguientes indicadores se pueden usar de forma independiente y se pueden especificar en cualquier orden.

| Argumento | Descripción |
| --- | --- |
| BOOT | **(Opcional)** Marque la nueva imagen como la imagen "de arranque" del archivo WIM. |
| CHECK | **(Opcional)** Incluir información de integridad adicional en el archivo WIM resultante.  |
| NOACL | **(Opcional)** No capture descriptores de seguridad en archivos y directorios. |

## Observaciones

Integridad de los datos: los archivos WIM incluyen sumas de verificación de todos los datos de archivos. Además, un archivo WIM puede incluir una tabla de integridad (sumas de comprobación adicionales) sobre los datos brutos de todo el archivo WIM. Por razones de rendimiento, PEBakery no crea la tabla de integridad de forma predeterminada, pero el indicador `CHECK` se puede especificar para que lo haga.

Este comando usa la [biblioteca de imágenes de Windows de código abierto (wimlib)](https://wimlib.net/).

## Relacionado

[WimMount](./WimMount.md), [WimUnmount](./WimUnmount.md), [WimAppend](./WimAppend.md)

## Ejemplos

### Ejemplo 1

Cree un archivo .wim de arranque usando la compresión _LZX_ de _C:\Temp\Target_

```pebakery
WimCapture,C:\Temp\Target,C:\Temp\Target\TEST.WIM,LZX,ImageName="MyBootImage",BOOT
```
