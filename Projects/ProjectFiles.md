# Archivos Script.Project

El archivo `Script.Project` define un proyecto.

Cada proyecto tiene un archivo script.project y solo uno que puede contener variables, macros, comandos, archivos codificados y posiblemente una interfaz gráfica de usuario (GUI) que conforman la base del proyecto.

## Ubicación del archivo

El archivo debe estar ubicado en una subcarpeta (generalmente coincidiendo con el `Título` del proyecto) del directorio `Proyectos` de PEBakery.

```
C:\PEBakery\
|--- Projects\
     |--- myProject\
          |--- script.project
     |--- Tools\
|--- Launcher.exe
|--- PEBakery.ini
```

## Formato de archivo

Los archivos Script.project son archivos de texto con el nombre `script.project` y están formados por "Secciones" muy similar a un archivo _.ini_ estándar. Como mínimo, un archivo script.project debe contener una sección `Main` que defina el` Title` de su proyecto para que aparezca en _Project Tree_ de PEBakery. Todos los archivos .script bajo la estructura de directorios de script.project se cargarán como nodos secundarios bajo el proyecto `Title`.

## Secciones

La estructura de un archivo script.project consta de 4 secciones principales. El autor del proyecto puede definir secciones adicionales para incluir comandos adicionales, interfaces o archivos incrustados.

### Secciones principales

Las siguientes secciones definen el comportamiento y las acciones del script. Haga clic en el nombre de una "Sección" para más detalles.

| Sección | Descripción |
| --- | --- |
| [Main](./ProjectMain.md) | La sección principal que define tu script. |
| [Interface](./ScriptInterface.md) | **(Opcional)** La sección Interfaz contiene una o más líneas que definen los controles de la Interfaz gráfica de usuario de un script.  |
| [Process](./ProjectProcess.md) | **(Opcional)** Esta sección contiene la lógica principal del script y se procesa al presionar el botón `Build`. |
| [Variables](./ProjectVariables.md) | **(Opcional)** Esta sección se usa para declarar variables predefinidas y macros utilizadas por el script en tiempo de ejecución. |

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

[Script Commands](/Commands/Script/README.md), [Script Files (.script)](./ScriptFiles.md)
