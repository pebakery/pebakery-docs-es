# AddVariables (Agregar variables)

Leer variables de otra sección, script o archivo en el entorno de tiempo de ejecución del script actual.

## Sintaxis

```pebakery
AddVariables,<FileName>,<Section>,[GLOBAL]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| FileName | La ruta completa del archivo para leer. **Sugerencia:** Use `%ScriptFile%` para hacer referencia al script actual.|
| Section | La sección que contiene las variables que se agregarán. |

### Flags (Indicadores)

| Flag | Descripción |
| --- | --- |
| GLOBAL | **(Opcional)** Las variables se agregan al alcance global y están disponibles para todo el proyecto durante la construcción. Si las variables existen, se sobrescribirán. |

## Observaciones

Cuando se ejecuta un script, agrega automáticamente las variables definidas en la sección `[Variables]` del script. El comando `AddVariables` le da la flexibilidad de agregar variables adicionales almacenadas en otros scripts y archivos y se puede usar en *script.project* para cargar variables y macros para todo el proyecto.

## Relacionado
[Set](./Set.md), [SetMacro](./SetMacro.md)

## Ejemplos

### Ejemplo 1

```pebakery
// Agregar variables de otra sección en el script actual
AddVariables,%ScriptFile%,AlternativeVariables
```

### Ejemplo 2

El siguiente código si se coloca en *script.project* cargará las macros definidas en una "biblioteca" de scripts para que las use todo el proyecto.

```pebakery
// Agregue macros de otro script para que estén disponibles para todos los scripts
AddVariables,%BaseDir%\Build\Library.script,ApiVar,GLOBAL
```
