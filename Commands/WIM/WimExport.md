# WimExport

Exporta una imagen desde un archivo WIM.

## Sintaxis

```pebakery
WimExport,<SrcWim>,<ImageIndex>,<DestWim>,[ImageName=<String>],[ImageDesc=<String>],[Split=<String>],[Recomp=<String>],[BOOT],[CHECK|NOCHECK]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| SrcWim | La ruta completa del archivo .wim que contiene la imagen para exportar. |
| ImageIndex | El índice de la imagen que se exportará. |
| DestWim | La ruta completa al archivo .wim que se está creando. Si el archivo WIM existe, será reconstruido. El proceso de reconstrucción es más lento que simplemente agregar la imagen, pero se ahorrará espacio que de otro modo quedaría como un agujero en el WIM. Si la estructura del directorio no existe, se creará. |
| ImageName= | **(Opcional)** El nombre único para la imagen que se está exportando. Si no se especifica, se usará de manera predeterminada el nombre de la imagen utilizada en `SrcWim`. |
| ImageDesc= | **(Opcional)** Información adicional sobre la imagen. Si no se especifica, se usará de manera predeterminada la descripción utilizada en `SrcWim`. |
| Split= | **(Opcional)** Una cadena que consiste en un archivo de estilo shell "GLOB" que especifica las partes adicionales del WIM dividido. El GLOB debe expandirse para incluir todas las partes del WIM dividido. Los comodines (? *) Son compatibles. |
| ReComp= | **(Opcional)** Vuelve a comprimir (optimizar) todos los datos en el WIM. Esto aumentará significativamente el tiempo necesario para optimizar el WIM, pero puede dar como resultado una mejor relación de compresión si la imagen original no se creó usando Wimlib. Especifique uno de los siguientes algoritmos de compresión: |
|| KEEP - Conservar el formato de compresión existente. **Debe elegir esta opción si `DestWim` ya existe.** Si necesita cambiar la compresión en un archivo wim existente, puede ejecutar` WimOptimize` en `DestWim` después de exportarlo. |
|| NONE - Sin Compresión. |
|| XPRESS - Compresión y descompresión rápidas, pero da como resultado un tamaño de imagen más grande. _(Similar a DISM.exe  /compress:fast )_ |
|| LZX - Zip estilo DEFLATE compresión. _(Similar a DISM.exe: /compress:maximum)_ |
|| LZMS - Formato de compresión no documentado de Microsoft similar al algoritmo LZMA utilizado por 7zip. Tamaño de imagen más pequeño, pero toma mucho más tiempo para comprimir. _(Similar a DISM.exe /compress:recovery)_ |

### Flags (Indicadores)

| Argumento | Descripción |
| --- | --- |
| BOOT | **(Opcional)** Marque la nueva imagen como la imagen "de arranque" del archivo WIM. |
| CHECK | **(Opcional)** Antes de optimizar el WIM, verificar su integridad si contiene información de integridad adicional. Incluir también información de integridad adicional en el WIM optimizado, incluso si no estaba presente antes.  |
| NOCHECK | **(Opcional)** No incluir información de integridad adicional en el WIM optimizado, incluso si ya estaba presente. |

Los indicadores `CHECK` y` NOCHECK` son mutuamente excluyentes.

## Observaciones

**Deduplicación de datos:** El formato WIM tiene deduplicación incorporada (también llamada "instancia única") del contenido del archivo. Por lo tanto, cuando se exporta una imagen, solo se copiarán físicamente los contenidos del archivo que no estén presentes en el WIM de destino. Sin embargo, siempre se creará una nueva copia del recurso de metadatos de la imagen, que describe la estructura del directorio de la imagen.

**Integridad de datos:** Para detectar daños accidentales (no maliciosos) en los datos, se calcula la suma de comprobación de cada archivo extraído y se devuelve un error si no coincide con la suma de comprobación incluida en el archivo WIM. Además, un archivo WIM puede incluir una tabla de integridad (sumas de comprobación adicionales) sobre los datos brutos de todo el archivo WIM. Por razones de rendimiento, PEBakery no verifica ni crea la tabla de integridad de manera predeterminada, pero se puede especificar el indicador `CHECK` para que lo haga.

**Archivos ESD:** PEBakery puede exportar imágenes desde WIM comprimidos sólidos o archivos "ESD" (.esd), al igual que los archivos WIM (.wim) normales. Sin embargo, a veces Microsoft distribuye archivos ESD con segmentos cifrados; PEBakery no puede exportar tales imágenes hasta que hayan sido descifradas.

**WIMs divididos:** PEBakery admite exportar imágenes de (pero no a) divididos archivos WIM (.swm) usando el argumento `Split =`.

Este comando usa la [biblioteca de imágenes de Windows de código abierto (wimlib)](https://wimlib.net/).

## Relacionado

[WimAppend](./WimAppend.md), [WimCapture](./WimCapture.md), [WimOptimize](./WimOptimize.md), [WimPathAdd](./WimPathAdd.md), [WimPathDelete](./WimPathDelete.md), [WimPathRename](./WimPathRename.md)

## Ejemplos

### Ejemplo 1

Exportar la imagen 4 desde *install.wim* a un nuevo archivo *Install1.wim*.

```pebakery
WimExport,C:\Temp\Install.wim,4,C:\Temp\Install1.wim
```

### Ejemplo 2

Exportar imagen 4 desde el WIM dividido *install.swm* a un archivo *Install2.wim* existente y volver a comprimir utilizando el formato de compresión existente.

```pebakery
WimExport,C:\Temp\Install.swm,4,C:\Temp\Install2.wim,ReComp=KEEP,Split="C:\Temp\install*.swm"
```

### Ejemplo 3

Exportar la imagen 4 de *install.wim* a un nuevo *install3.wim* y volver a comprimir utilizando la compresión LZMS.

```pebakery
WimExport,C:\Temp\Install.wim,4,C:\Temp\Install3.wim,ReComp=LZMS
// Renombrar a un install.esd
FileRename,C:\Temp\install2.wim,C:\Temp\install3.esd
```
