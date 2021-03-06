# Proyecto sección [Main] (Principal)

La sección principal que define todos los detalles de su proyecto.

Esta documentación se refiere a la sección `Principal` ubicada dentro del archivo `script.project`. Para la documentación relacionada con la sección `Main` de scripts individuales, consulte` Script Main`.

## Sintaxis

Los datos del proyecto se almacenan en formato estilo .INI `Key=Value` `(Clave=Valor)`.

## Valores

Los siguientes valores son utilizados por PEBakery para definir un proyecto. Los desarrolladores de proyectos pueden definir valores adicionales bajo la sección `[Main]` para otros usos. Estos valores serán ignorados por PEBakery.

| Nombre | Descripción |
| --- | --- |
| Title | El título de tu proyecto. |
| Description | **(Opcional)** Una breve descripción del proyecto. |
| Author | **(Opcional)** El autor del proyecto. |
| Credits | **(Opcional)** Reconocimiento de personas o equipos que contribuyeron al desarrollo del proyecto. |
| Date | **(Opcional)** Fecha en que el proyecto fue lanzado. (El formato recomendado es YYYY-MM-DD.) |
| Version | **(Opcional)** Número de versión del proyecto. |
| Interface | **(Opcional)** Especifica la sección que contiene la Interfaz gráfica de usuario que se muestra actualmente. El valor predeterminado es `Interface`. |
| PathSetting | `True`/`False` - Habilite la modificación de `SourceDir`,` TargetDir`, e `IsoFile` desde el cuadro de diálogo Configuración de PEBakery. |
| SourceDir | **(Legacy)** Ruta completa a los archivos fuente de Windows utilizados para construir el proyecto. Si `PathSetting = True` el valor se copia en la variable `GLOBAL` `%SourceDir%` al momento de la compilación. |
| TargetDir | **(Legacy)** Ruta completa al directorio donde se construirá el proyecto. Si `PathSetting = True` el valor se copia en la variable `GLOBAL` `%TargetDir% `en el momento de la compilación. |
| IsoFile | **(Legacy)** Ruta completa al archivo .iso que se generará. Si `PathSetting = True` el valor se copia en la variable `GLOBAL` `%IsoFile% `en el momento de la compilación. |

`SourceDir`, `TargetDir`, e `IsoFile` se incluyen para compatibilidad con Winbuilder 082. No son necesarios para proyectos PEBakery, que generalmente almacenan sus rutas en una variable GLOBAL.

## Observaciones

Ninguna.

## Relacionado

[Project Process](./ProjectProcess.md), [Project Variables](./ProjectVariables.md), [Script Interface](./ScriptInterface.md), [Script Main](./ScriptMain.md), [Script Process](./ScriptProcess), [Script Variables](./ScriptVariables.md)

## Ejemplos

### Ejemplo 1

Una típica sección `Main` `(Principal)` de un proyecto.

```pebakery
[Main]
Title=MyWinPE
Description=My PEBakery project
Author=James Bond
Version=1
Date=2018.02.10
PathSetting=False
```

### Ejemplo 2

Una típica sección `Main` `(Principal)` de un "proyecto heredado".

```pebakery
[Main]
Title=Win7PE SE
Description=Win7PE_SE project that supports Win7 DVD x86 and x64
Author=NightMan, YahooUK, JFX, ChrisR
Version=15
Date=2011.02.10
SourceDir=D:\Images\Win7
TargetDir=%baseDir%\Target\Win7PE_SE
ISOfile=%baseDir%\ISO\Win7Pe.iso
```
