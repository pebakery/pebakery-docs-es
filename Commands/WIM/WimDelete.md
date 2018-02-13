# WimDelete

Eliminar una imagen desde un archivo de imagen de Windows (.wim).

`WimDelete` reconstruye el WIM con todos los datos de archivo innecesarios eliminados. Esto es diferente de ImageX y DISM de Microsoft, que solo borrará los metadatos del árbol de directorios y los datos XML, dejando intactos los datos del archivo.

## Sintaxis

```pebakery
WimDelete,<WimFile>,<ImageIndex>[,CHECK]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| WimFile | La ruta completa al archivo .wim. |
| ImageIndex | El índice de la imagen dentro del archivo WIM para eliminar. |

### Flags (Indicadores)

| Argumento | Descripción |
| --- | --- |
| CHECK | **(Opcional)** Antes de eliminar una imagen del WIM, verificar su integridad si contiene información de integridad adicional. Incluir también información de integridad adicional en el WIM reconstruido, incluso si no estaba presente antes.  |

## Observaciones

Es posible eliminar todas las imágenes de un WIM y tener un WIM con 0 imágenes, aunque tal archivo puede no ser muy útil.

**Integridad de datos:** Para detectar daños accidentales (no maliciosos) en los datos, se calcula la suma de comprobación de cada archivo extraído y se devuelve un error si no coincide con la suma de comprobación incluida en el archivo WIM. Además, un archivo WIM puede incluir una tabla de integridad (sumas de comprobación adicionales) sobre los datos brutos de todo el archivo WIM. Por razones de rendimiento, PEBakery no verifica ni crea la tabla de integridad de manera predeterminada, pero se puede especificar el indicador `CHECK` para que lo haga.

**WIMs divididos:** PEBakery no admite la eliminación de imágenes de archivos WIM divididos (.swm).

Este comando usa la [biblioteca de imágenes de Windows de código abierto (wimlib)](https://wimlib.net/).

## Relacionado

[WimMount](./WimMount.md), [WimUnmount](./WimUnmount.md), [WimAppend](./WimAppend), [WimInfo](./WimInfo.md), [WimPathDelete](./WimPathDelete.md)

## Ejemplos

### Ejemplo 1

En este ejemplo, eliminaremos la primera imagen (índice 1) en un archivo WIM.

```pebakery
WimDelete,C:\Temp\Boot.wim,1
```
