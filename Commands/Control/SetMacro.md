# SetMacro (Establecer Macro)

Define un procedimiento que se ejecutará cuando se encuentre una palabra clave específica.

Las macros simplifican el mantenimiento de los scripts ya que el código se escribe solo una vez, pero se puede invocar repetidamente por cualquier cantidad de scripts o procesos. Son ideales para tareas repetitivas, como crear accesos directos o descargar y desempaquetar un archivo.

## Sintaxis

```pebakery
SetMacro,<MacroName>,<MacroCommand>[,GLOBAL | PERMANENT]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| MacroName | El nombre de nuestra macro. `MacroName` solo puede contener los siguientes caracteres `a-z A-Z 0-9 _ ( ) .` Dado que las macros se analizan antes del tiempo de ejecución usar %Variables% en el nombre de la macro no es compatible.|
| MacroCommand | El comando que se ejecutará cuando se llame a la macro. `MacroCommand` debe estar entre comillas dobles. Establecer este argumento a `NIL` eliminará la macro. |

### Flags (Indicadores)

Los siguientes indicadores (flags) son mutuamente excluyentes.

| Flag | Descripción |
| --- | --- |
| GLOBAL | Almacena la macro en la memoria global durante el tiempo de vida del proceso de compilación. Esto permitirá que otros scripts hagan referencia y/o modifiquen esta macro. Si la macro ya está definida, se sobrescribirá. |
| PERMANENT | Almacena permanentemente el valor de esta variable escribiendo la definición en la sección [Variables] de script.project. If the macro is already defined it will be overwritten. |

## Observaciones

Las macros pueden ser tan simples como un solo comando o se puede definir un procedimiento complejo colocando la macro en su propia [Sección] y llamándola con el comando `Ejecutar`(Run).

Las macros globales y permanentes solo se pueden eliminar si se configura el indicador `GLOBAL` o `PERMANENT` respectivo.

## Relacionado

[AddVariables](./AddVariables.md)

## Ejemplos

### Ejemplo 1

El siguiente ejemplo crea una macro para replicar el comando obsoleto WebGetIfNotExist. Esto nos permite llamar a nuestra macro varias veces dentro del script o llamarla desde otro script mientras mantenemos el código en una ubicación central.

```pebakery
[Main]
Title=SetMacro (Establecer Macro) Ejemplo
Description=Mostrar el uso del comando SetMacro
Author=Homes32
Level=5
Version=1

[Variables]

[Process]
// Definir nuestra macro 'WebGetIfNotExistEx'
SetMacro,WebGetIfNotExistEx,"Run,%ScriptFile%,WebGetIfNotExistEx"

// Llamar a nuestra macro
WebGetIfNotExistEx,"https://zlib.net/zlib-1.2.11.tar.gz",%BaseDir%\zlib.tar.gz

// Esta es la sección que se ejecutará cuando se llame a nuestra macro
[WebGetIfNotExistEx]
// Sintaxis: WebGetIfNotExistEx,<URL>,<DestFile>
Echo,"Checking for #2..."
If,Not,ExistFile,#2,Begin
// El archivo no existe. ¡Vamos a descargarlo!
Echo,"Descargando #2..."
WebGet,#1,#2
End
Else,Begin
// El archivo ya existe en el disco.
Echo,"#2 encontrado omitiendo la descarga."
End
```
