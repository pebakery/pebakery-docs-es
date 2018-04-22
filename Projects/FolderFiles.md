# Folder.Project Files

`Folder.Project` los archivos definen propiedades y comportamiento adicionales para las carpetas en PEBakery.

## Ubicación del archivo

El archivo debe estar ubicado en una subcarpeta del directorio `Projects` de PEBakery.

```text
C:\PEBakery\
|--- Projects\
     |--- myProject\
     |--- Build\
              |---my.script
              |---folder.project
              |--- folder.project
     |--- Tools\
|--- Launcher.exe
|--- PEBakery.ini
```

## Formato de archivo

Folder.project son archivos de texto con el nombre `folder.project` y están formados por "Secciones" muy similares a un archivo _.ini_ estándar.

## Secciones

La estructura de un archivo folder.project consta de 1 sección principal. Secciones adicionales pueden ser definidas por el autor del proyecto, pero serán ignoradas por PEBakery. Las secciones `[Interface]`, `[Process]` y `[Variable]` no son compatibles.

Mientras que los archivos `Folder.project` pueden contener técnicamente código que se puede ejecutar con los comandos `Run` o `Exec`, se desaconseja encarecidamente utilizar los archivos `Folder.Project` como biblioteca de códigos.

### [Enlaces]

Contiene una lista de rutas para importar. Se pueden especificar múltiples rutas, una por línea. Se considera que las rutas de enlace son relitivas al `% BaseDir%` a menos que se especifique una ruta absoluta.

Todos los scripts en la carpeta especificada y cualquier subcarpeta se agregarán a la carpeta que contiene el archivo `folder.project`. Si alguno de los scripts vinculados está deshabilitada, ese script también se desactivará en el proyecto de origen. Los caracteres comodín `*. *` Al final de la ruta son compatibles para compatibilidad con Winbuilder pero no son necesarios.

## Observaciones

Cualquier cambio realizado en un script vinculado modificará el archivo .script original.

## Relacionado

[.Link Files](./LinkFiles.md)

## Ejemplos

### Ejemplo 1

Este ejemplo vincula a varias carpetas relativas al `% BaseDir%` (para este ejemplo, se supone que es _C:\PEBakery\\_).

```pebakery
[Links]
Projects\Win10PESE\Apps\File Tasks
Projects\Win10PESE\Apps\HD Tasks\*.*
```

### Ejemplo 2

Este ejemplo se vincula a una ruta absoluta.

```pebakery
[Links]
D:\MyScripts
C:\PEBakery\Projects\Win10PESE\Apps\HD Tasks\*.*
```
