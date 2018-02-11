# Script sección [Principal]

La sección principal que define todos los detalles de su script. Estos datos afectan la forma en que se muestran las secuencias de comandos en la interfaz de usuario de PEBakery, así como la forma en que se procesa durante una compilación.

Esta documentación se refiere a la sección `Principal` ubicada dentro de los archivos `.script`. Para la documentación relacionada con la sección `Main` de `script.project`, consulte `Project Main`.

## Sintaxis

Los datos de script se almacenan en formato de estilo .INI `Clave=valor`.

## Valores

Los siguientes valores son utilizados por PEBakery para definir un script y su comportamiento. Los desarrolladores de scripts pueden definir valores adicionales bajo la sección `[Main]` para otros usos. Estos valores serán ignorados por PEBakery.

| Nombre | Descripción |
| --- | --- |
| Title | El título de tu script. |
| Description | **(Opcional)** Una breve descripción del propósito de los scripts. |
| Author | **(Opcional)** El autor del script. |
| Credits | **(Opcional)** Reconocimiento de personas o equipos que contribuyeron al desarrollo del guión. |
| Date | **(Opcional)** Fecha en que se lanzó el script. (El formato recomendado es YYYY-MM-DD.) |
| Version | **(Opcional)** Número de versión del script. |
| [Level](./ScriptLevel.md) | Define la secuencia en la que se procesa el script. **Por defecto** es `0`.|
| Selected | **(Opcional)** Define cómo se puede seleccionar el script para procesarlo. **Por defecto** es `True`. |
|| True - El script se selecciona en el árbol del proyecto y se procesará. |
|| False - El script no está seleccionado en el árbol del proyecto y no se procesará. |
|| None - El scripts no está permitido para ser seleccionada/deseleccionada y no será procesada. Utilizado principalmente para scripts de configuración y utilidad. |
| Interface | **(Opcional)** Especifica la sección que contiene la interfaz gráfica de usuario actualmente mostrada del script. El valor predeterminado es `Interface`. |
| Mandatory | **(Opcional)** El script se procesará y no se puede deshabilitar. **Por defecto** es `False`.|

## Observaciones

Ninguna.

## Relacionado

[Project Main](./ProjectMain.md), [Project Process](./ProjectProcess.md), [Project Variables](./ProjectVariables.md), [Script Interface](./ScriptInterface.md), [Script Process](./ScriptProcess), [Script Variables](./ScriptVariables.md), [Script Levels](./ScriptLevels.md)

## Ejemplos

### Ejemplo 1

Una típica sección 'Main' para una secuencia de comandos de la aplicación.

```pebakery
[Main]
Title=My App Script
Description=Agrega myApp al proyecto.
Author=Homes32
Credits=¡Gracias a ied206 por crear PEBakery!
Selected=True
Level=5
Version=1
Date=2018-02-08
```
