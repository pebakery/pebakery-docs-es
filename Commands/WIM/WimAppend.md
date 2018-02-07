# WimAppend

Añadir una imagen a un archivo existente de imágenes de Windows (.wim).

## Sintaxis

```pebakery
WimAppend,<SrcDir>,<DestWim>,<Compress>[,ImageName=<String>][,ImageDesc=<String>][,Flags=<String>][,DeltaIndex=<Integer>][,BOOT][,CHECK][,NOACL]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| SrcWim | La ruta completa a los archivos de origen que se capturarán. |
| DestWim | La ruta completa al archivo .wim que se está creando. Si el archivo existe, se sobrescribirá. Si la estructura del directorio no existe, se creará. |
| ImageName= | **(Opcional)** El nombre único para la imagen que se está capturando. Si no se especifica, se usará de forma predeterminada el componente de nombre de archivo de `SrcWim`. |
| ImageDesc= | **(Opcional)** Información adicional sobre la imagen. |
| Flags= | **(Opcional)** Especifique una cadena para usar en el elemento `<FLAGS>` de los datos XML para la nueva imagen. |
| DeltaIndex= | **(Opcional)** Un entero que representa una imagen existente dentro del archivo `DestWim`. Cualquier dato de archivo que normalmente sería necesario archivar en el archivo WIM nuevo o actualizado se omite si ya está presente en la imagen `SrcWim` en la que se basa el delta. El archivo WIM resultante aún contendrá una copia completa de los metadatos de la imagen, pero esto generalmente es solo una pequeña fracción del tamaño total del archivo WIM. |

Los argumentos `DeltaIndex =`, `ImageName =`, `ImageDesc =`, y `Flags =` se pueden usar de forma independiente y se pueden especificar en cualquier orden.

### Flags (Indicadores)

Los siguientes indicadores se pueden usar de forma independiente y se pueden especificar en cualquier orden.

| Argumento | Descripción |
| --- | --- |
| BOOT | **(Opcional)** Marcar la nueva imagen como la imagen "de arranque" del archivo WIM. |
| CHECK | **(Opcional)** Incluir información de integridad adicional en el archivo WIM resultante.  |
| NOACL | **(Opcional)** No capturar descriptores de seguridad en archivos y directorios. |

## Observaciones

Integridad de los datos: los archivos WIM incluyen sumas de verificación de todos los datos de archivos. Además, un archivo WIM puede incluir una tabla de integridad (sumas de comprobación adicionales) sobre los datos brutos de todo el archivo WIM. Por razones de rendimiento, PEBakery no crea la tabla de integridad de forma predeterminada, pero el indicador `CHECK` se puede especificar para que lo haga.

Nota: Se ha observado que el modo `--update-of` de wimlib utilizado por el argumento `DeltaIndex` no es completamente confiable para detectar cambios en los contenidos del archivo, lo que a veces hace que se archiven los antiguos contenidos de unos pocos archivos en lugar de los actuales contenido. La causa de este problema es que Windows no actualiza inmediatamente la última marca de tiempo de modificación de un archivo después de cada escritura en ese archivo. Desafortunadamente, no hay forma conocida de que aplicaciones como wimlib solucionen automáticamente este error. Soluciones manuales son posibles; teóricamente, realizar cualquier acción que provoque el cierre de los archivos problemáticos, como reiniciar aplicaciones o la computadora misma, debe hacer que se actualicen las últimas marcas de fecha y hora de modificación del archivo. También tenga en cuenta que wimlib compara los tamaños de archivo y las marcas de tiempo para determinar si un archivo ha cambiado, lo que ayuda a que el problema sea menos probable que ocurra.

WIM divididos: PEBakery no admite anexar archivos WIM divididos (.swm).

Este comando usa la [biblioteca de imágenes de Windows de código abierto (wimlib)](https://wimlib.net/).

## Relacionado

[WimMount](./WimMount.md), [WimUnmount](./WimUnmount.md), [WimCapture](./WimCapture.md)

## Ejemplos

### Ejemplo 1

Capture data into an existing .wim file.

```pebakery
WimAppend,"C:\Temp\Target","C:\Temp\Target\TEST.WIM"
```
