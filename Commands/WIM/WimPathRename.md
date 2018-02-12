# WimPathRename

Mover o Renombrar un archivo o árbol de directorios en un archivo de imagen de Windows (.wim).

## Sintaxis

```pebakery
WimPathRename,<WimFile>,<ImageIndex>,<SrcPath>,<DestPath>[,CHECK][,REBUILD]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| WimFile | La ruta completa del archivo .wim para modificar. |
| ImageIndex | El índice de la imagen dentro del archivo .wim donde reside el archivo o directorio. |
| SrcPath |  La ruta completa del archivo o directorio a cambiar de nombre. Todas las rutas son relativas al directorio raíz de la imagen. Si `SrcPath` no existe, la operación fallará. |
| DestPath | La ruta completa a la nueva ubicación del archivo o directorio dentro del archivo WIM. Todas las rutas son relativas al directorio raíz de la imagen. Se sobrescribirán todos los archivos o directorios existentes. Si la estructura del directorio no existe, se creará. |

### Flags (Indicadores)

Los siguientes indicadores se pueden usar de forma independiente y se pueden especificar en cualquier orden.

| Argumento | Descripción |
| --- | --- |
| CHECK | **(Opcional)** Antes de actualizar `WimFile`, verificar su integridad si contiene información de integridad adicional. Incluye también información de integridad adicional en el WIM actualizado, incluso si no estaba presente antes. |
| REBUILD | **(Opcional)** Reconstruir todo el WIM en lugar de anexar los datos al final de la imagen. Reconstruir el WIM es más lento, pero recuperará espacio que de otro modo quedaría como un agujero en el archivo WIM. |

## Observaciones

**Integridad de datos:** Para detectar daños accidentales (no maliciosos) en los datos, se calcula la suma de comprobación de cada archivo extraído y se devuelve un error si no coincide con la suma de comprobación incluida en el archivo WIM. Además, un archivo WIM puede incluir una tabla de integridad (sumas de comprobación adicionales) sobre los datos brutos de todo el archivo WIM. Por razones de rendimiento, PEBakery no verifica ni crea la tabla de integridad de manera predeterminada, pero se puede especificar el indicador `CHECK` para que lo haga.

Este comando usa la [biblioteca de imágenes de Windows de código abierto (wimlib)](https://wimlib.net/).

## Relacionado

[WimMount](./WimMount.md), [WimUnmount](./WimUnmount.md), [WimPathAdd](./WimPathAdd.md), [WimPathDelete](./WimPathDelete.md)

## Ejemplos

### Ejemploe 1

Este ejemplo cambia el nombre de un solo archivo en la primera imagen de *C:\Temp\boot.wim*.

```pebakery
Echo,"Renombrar archivo..."
WimPathRename,C:\Temp\boot.wim,1,Windows\regedit.exe,Windows\regedit2.exe
```

### Ejemplo 2

Este ejemplo moverá el directorio */Program Files/myApp* en la primera imagen de *C:\Temp\boot.wim* to /Programs/myApp.

```pebakery
Echo,"Moviendo directorio..."
WimPathRename,C:\Temp\boot.wim,1,"/Program Files/myApp","/Programs/myApp"
```
