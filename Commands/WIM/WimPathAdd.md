# WimPathAdd

Agregar un archivo o árbol de directorios a un archivo de imagen de Windows (.wim).

## Sintaxis

```pebakery
WimPathAdd,<WimFile>,<ImageIndex>,<SrcPath>,<DestPath>[,CHECK][,NOACL][,PRESERVE][,REBUILD]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| WimFile | La ruta completa del archivo .wim para modificar. |
| ImageIndex | El índice de la imagen dentro del archivo .wim donde se agregarán los archivos. |
| SrcPath |  La ruta completa del archivo o directorio para agregar a la imagen. |
| DestPath | La ruta completa al archivo o directorio dentro del archivo WIM. Si `SrcPath` es un archivo, `DestPath` debe ser un archivo. Si `SrcPath` es un directorio, `DestPath` debe ser un directorio. Todas las rutas son relativas al directorio raíz de la imagen. Todos los archivos duplicados existentes se sobrescribirán a menos que se especifique el indicador `PRESERVE` `(PRESERVAR)`. Si la estructura del directorio no existe, se creará. |

### Flags (Indicadores)

Los siguientes indicadores se pueden usar de forma independiente y se pueden especificar en cualquier orden.

| Argumento | Descripción |
| --- | --- |
| CHECK | **(Opcional)** Antes de actualizar `WimFile`, verificar su integridad si contiene información de integridad adicional. Incluye también información de integridad adicional en el WIM actualizado, incluso si no estaba presente antes. |
| NOACL | **(Opcional)** No conservar las descripciones de seguridad de archivos y directorios. |
| PRESERVE | **(Opcional)** No sobrescribir los archivos existentes. |
| REBUILD | **(Opcional)** Reconstruir todo el WIM en lugar de anexar los datos al final de la imagen. Reconstruir el WIM es más lento, pero recuperará espacio que de otro modo quedaría como un agujero en el archivo WIM. |

## Observaciones

**Integridad de datos:** Para detectar daños accidentales (no maliciosos) en los datos, se calcula la suma de comprobación de cada archivo extraído y se devuelve un error si no coincide con la suma de comprobación incluida en el archivo WIM. Además, un archivo WIM puede incluir una tabla de integridad (sumas de comprobación adicionales) sobre los datos brutos de todo el archivo WIM. Por razones de rendimiento, PEBakery no verifica ni crea la tabla de integridad de manera predeterminada, pero se puede especificar el indicador `CHECK` para que lo haga..

Este comando usa la [biblioteca de imágenes de Windows de código abierto (wimlib)](https://wimlib.net/).

## Relacionado

[WimMount](./WimMount.md), [WimUnmount](./WimUnmount.md), [WimPathDelete](./WimPathDelete.md), [WimPathRename](./WimPathRename.md)

## Ejemplos

### Ejemplo 1

Este ejemplo agrega un solo archivo a la primera imagen de *C:\Temp\boot.wim*.

```pebakery
Echo,"Agregando archivo..."
WimPathAdd,C:\Temp\boot.wim,1,C:\Windows\regedit.exe,Windows\regedit.exe
```

### Ejemplo 2

Este ejemplo agregará el directorio *C:\Temp\Files* a la primera imagen de *C:\Temp\boot.wim*.

```pebakery
Echo,"Agregando directorio..."
WimPathAdd,C:\Temp\boot.wim,1,C:\Temp\Files,"/Program Files/myApp"
```
