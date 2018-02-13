# WimOptimize

Reconstruir un archivo de imagen de Windows (.wim).

La reconstrucción eliminará cualquier agujero que haya quedado en el WIM como resultado de agregar o eliminar archivos o imágenes, por lo que el nuevo WIM puede ser más pequeño que el antiguo WIM.

Por defecto, `WimOptimize` reutilizará datos comprimidos existentes, sin embargo, también es posible volver a comprimir el archivo WIM utilizando otro algoritmo durante el proceso de reconstrucción.

## Sintaxis

```pebakery
WimOptimize,<WimFile>[,RECOMPRESS[=<STR>]][,CHECK|NOCHECK]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| WimFile | La ruta completa del archivo .wim para optimizar. |
| RECOMPRESS= | **(Opcional)** Recomprimir todos los datos en el WIM. Esto aumentará significativamente el tiempo necesario para optimizar el WIM, pero puede dar como resultado una mejor relación de compresión si la imagen original no se creó usando Wimlib. Para reconstruir el WIM con el formato de compresión existente, use `RECOMPRESS`. Para cambiar el algoritmo de compresión, use `RECOMPRESS=` y especifique uno de los siguientes algoritmos de compresión: |
|| NONE - Sin Compresión. |
|| XPRESS - Compresión y descompresión rápidas, pero da como resultado un tamaño de imagen más grande. _(Similar a DISM.exe  /compress:fast )_ |
|| LZX - Estilo Zip Compresión DEFLATE. _(Similar a DISM.exe: /compress:maximum)_ |
|| LZMS - Formato de compresión no documentado de Microsoft similar al algoritmo LZMA utilizado por 7zip. Tamaño de imagen más pequeño, pero toma mucho más tiempo para comprimir. _(Similar a DISM.exe /compress:recovery)_ |

### Flags (Indicadores)

Las siguientes flags son mutuamente excluyentes.

| Argumento | Descripción |
| --- | --- |
| CHECK | **(Opcional)** Antes de optimizar el WIM, verificar su integridad si contiene información de integridad adicional. Incluir también información de integridad adicional en el WIM optimizado, incluso si no estaba presente antes.  |
| NOCHECK | **(Opcional)** No incluir información de integridad adicional en el WIM optimizado, incluso si estuvo presente antes. |

## Observaciones

**Integridad de los datos:** Para detectar daños accidentales (no maliciosos) en los datos, se calcula la suma de comprobación de cada archivo extraído y se devuelve un error si no coincide con la suma de comprobación incluida en el archivo WIM. Además, un archivo WIM puede incluir una tabla de integridad (sumas de comprobación adicionales) sobre los datos brutos de todo el archivo WIM. Por razones de rendimiento, PEBakery no verifica ni crea la tabla de integridad de manera predeterminada, pero se puede especificar el indicador `CHECK` para que lo haga.

**WIMs divididos:** `WimOptimize` no es compatible con WIM divididos o WIM delta.

Este comando usa la [biblioteca de imágenes de Windows de código abierto (wimlib)](https://wimlib.net/).

## Relacionado

[WimAppend](./WimAppend.md), [WimCapture](./WimCapture.md), [WimPathAdd](./WimPathAdd.md), [WimPathDelete](./WimPathDelete.md), [WimPathRename](./WimPathRename.md)

## Ejemplos

### Ejemplo 1

Reconstruir *install.wim*.

```pebakery
WimOptimize,C:\Temp\Install.wim
```

### Ejemplo 2

Reconstruir y recomprimir *install.wim*.

```pebakery
WimOptimize,C:\Temp\Install.wim,RECOMPRESS
```

### Ejemplo 3

Reconstruir y recomprimir *install.wim* usando compresión LZX.

```pebakery
WimOptimize,C:\Temp\Install.wim,RECOMPRESS=LXZ
// Renombrar a install.esd
FileRename,C:\Temp\install.wim,C:\Temp\install.esd
```
