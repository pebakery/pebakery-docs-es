# Archivos .script

Los archivos .script son los bloques de construcción de un proyecto y contienen los comandos y la lógica necesarios para construir su PE.

Cada archivo .script puede contener variables, macros, comandos, archivos codificados y, posiblemente, una interfaz gráfica de usuario (GUI) que funcionan en conjunto para realizar diversas tareas; desde construir el núcleo del proyecto hasta agregar aplicaciones adicionales y configuración de ajustes.

## Ubicación del archivo

Los archivos .script deben estar ubicados en el directorio `Projects` de PEBakery, debajo de la carpeta respectiva del proyecto.

```
C:\PEBakery\
|--- Projects\
     |--- myProject\
          |--- script.project
          |--- Build\
               |--- myScript1.script
               |--- myScript2.script
          |--- myScript3.script
     |--- Tools\
|--- Launcher.exe
|--- PEBakery.ini
```

## Formato de archivo

Los archivos .Script son archivos de texto con una extensión `.script` y están formados por "Secciones" muy similar a un archivo _.ini_ estándar. Como mínimo, un archivo .script debe contener una sección `Main` que defina `Title` y `Level` de su script para que aparezca en _Project Tree_ de PEBakery.

## Secciones

La estructura de un archivo .script consta de 4 secciones principales. El autor del script puede definir secciones adicionales para incluir comandos adicionales, interfaces o archivos incrustados.

### Secciones principales

Las siguientes secciones definen el comportamiento y las acciones del script.

Haga clic en el nombre de una `Sección` para más detalles.

| Sección | Descripción |
| --- | --- |
| [Main](./ScriptMain.md) | La sección principal que define tu script. |
| [Interface](./ScriptInterface.md) | **(Opcional)** La sección Interfaz contiene una o más líneas que definen los controles de la Interfaz gráfica de usuario de un script.  |
| [Process](./ScriptProcess.md) | **(Opcional)** Esta sección contiene la lógica principal del script y se procesa al presionar el botón `Build`. |
| [Variables](./ScriptVariables.md) | **(Opcional)** Esta sección se usa para declarar variables predefinidas y macros utilizadas por el script en tiempo de ejecución. |

### Secciones internas

Las siguientes secciones son utilizadas internamente por PEBakery y no deben ser modificadas.
Para obtener más información sobre los archivos codificados, consulte `Comandos de script'.

| Sección | Descripción |
| --- | --- |
| EncodedFolders | Contiene una lista de carpetas que contienen archivos codificados. |
| _\<FolderName>_ | Contiene una lista de archivos contenidos dentro de la carpeta especificada. |
| EncodedFile-_\<FolderName>_-_\<FileName>_ | Contiene un archivo codificado. |
| InterfaceEncoded | Contiene una lista de archivos codificados utilizados por la interfaz gráfica de usuario del script |
| EncodedFile-InterfaceEncoded-_\<FileName>_ | Contiene el archivo codificado al que hace referencia `FileName` de la sección `InterfaceEncoded`. |
| AuthorEncoded | Define la imagen del logo del script. |
| EncodedFile-AuthorEncoded-_\<FileName>_ | Contiene el archivo codificado para la imagen del logotipo del script. |

## Observaciones

Ninguna.

## Relacionado

[Link Files](./LinkFiles.md), [Script Levels](.ScriptLevels.md), [Project File (script.project)](./ProjectFiles.md)
