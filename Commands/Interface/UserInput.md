# UserInput

**Alias**: `Retrieve,Dir` `Retrieve,File`

Solicita al usuario que seleccione una ruta de archivo o directorio.

## Sintaxis

```pebakery
UserInput,<BrowserType>,<InitPath>,<%DestVar%>
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| BrowserType | Uno de los siguientes tipos: |
|| FilePath - Mostrar un buscador de archivos. |
|| DirPath - Mostrar un navegador de directorio. |
| InitPath | La ruta de inicio y el filtro para el diálogo de exploración. |
| %DestVar% | La variable que contendrá la ruta completa del archivo o directorio seleccionado. |

## Observaciones

Puede forzar al usuario a elegir un tipo de archivo específico (es decir, un archivo .txt) especificando la extensión del archivo en `InitPath`. Múltiples filtros de tipo de archivo no son compatibles.

Si el usuario hace clic en el botón cancelar en el diálogo del navegador, la operación fallará.

## Relacionado

## Ejemplos

### Ejemplo 1

```pebakery
[main]
Title=UserInput Ejemplo
Description=Muestra el uso del comando UserInput.
Level=5
Version=1
Author=Homes32

[variables]

[process]
// Explorador de archivos que permite al usuario elegir cualquier tipo de archivo.
UserInput,FilePath,C:\.*,%var%
Message,"Usted seleccionó: %var%"

// Explorador de archivos que solo permite al usuario elegir archivos .txt.
UserInput,FilePath,C:\*.txt,%var%
Message,"Usted seleccionó: %var%"

// Navegador de directorios
UserInput,DirPath,C:\,%var%
Message,"Usted seleccionó: %var%"
```
