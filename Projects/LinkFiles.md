# .Link Files

Los archivos `.Link` son" enlaces simbólicos "que le permiten hacer referencia a archivos de script individuales que no se encuentran en el directorio de su proyecto.

## Ubicación del archivo

El archivo debe estar ubicado en una subcarpeta del directorio `Projects` de PEBakery.

```text
C:\PEBakery\
|--- Projects\
     |--- myProject\
     |--- Build\
              |---my.script
              |---myOtherScript.link
              |--- folder.project
     |--- Tools\
|--- Launcher.exe
|--- PEBakery.ini
```

## Formato de archivo

Los archivos de enlace son archivos de texto con la extensión `.link` y están formados por "Secciones" muy similar a un archivo _.ini_ estándar.
A diferencia de los "enlaces de carpeta" definidos por los archivos `folder.project`, los archivos `.link` almacenan el estado seleccionado en el archivo de enlace, lo que permite que un script vinculado a varios proyectos sea seleccionado independientemente por cada proyecto.

## Secciones

La estructura de un archivo de enlace consta de 1 sección principal. Secciones adicionales pueden ser definidas por el autor del proyecto, pero serán ignoradas por PEBakery. Las secciones `[Interface]`, `[Process]` y `[Variable]` no son compatibles.

Si bien los archivos de enlace pueden contener técnicamente código que se puede ejecutar con los comandos `Run` o `Ejecutar`, no se recomienda usar archivos de enlace como biblioteca de códigos.

### [Principal]

Los siguientes valores son utilizados por PEBakery para definir un enlace y su comportamiento. Los desarrolladores de scripts pueden definir valores adicionales bajo la sección `[Principal]` para otros usos. Estos valores serán ignorados por PEBakery.

| Nombre | Descripción |
| --- | --- |
| Link | 142/5000
La ruta al archivo .script para incluir en el proyecto. Las rutas se consideran relativas al `% BaseDir%` a menos que se especifique una ruta absoluta. |
|Selected | **(Opcional)** Define cómo se puede seleccionar el script para su procesamiento. El valor predeterminado es Verdadero. |
|| True - El script se selecciona en el árbol del proyecto y se procesará. |
|| False - El script no está seleccionado en el árbol del proyecto y no se procesará. |
|| None - El script no está permitido para ser seleccionado/deseleccionado y no será procesado. Se usa principalmente para scripts de configuración y utilidad. |

## Observaciones

Con la excepción de alternar el estado seleccionado a través del árbol de proyectos, cualquier cambio realizado en un script vinculado modificará el archivo .script original.

## Relacionado

[.Folder Files](./FolderFiles.md)

## Ejemplos

### Ejemplo 1

Este ejemplo vincula a varias carpetas relativas al `% BaseDir%` (para este ejemplo, se supone que es _C:\PEBakery\\_).

```pebakery
[Main]
Link=Projects\Addons\AccessGainDrivers.script
Selected=False
```

### Ejemplo 2

Este ejemplo se vincula a una ruta absoluta.

```pebakery
[Main]
Link=C:\MyScripts\Addons\AccessGainDrivers.script
Selected=True
```
