# System,RefreshScript

Actualice un script o ruta de acceso específica en el proyecto.

Los comodines (* ?) Son compatibles y se pueden usar para actualizar varios guiones a la vez.

## Sintaxis

```pebakery
System,RefreshScript,<FilePath>[,NOREC]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| FilePath | La ruta a un archivo de script ** existente ** para actualizar. Los comodines (* ?) Son compatibles.|

### Flags (Indicadores)

| Flag | Descripción |
| --- | --- |
| NOREC | **(Opcional)** No recurse a subdirectorios. |

## Observaciones

Este comando se puede utilizar para actualizar un script específico del árbol del proyecto y se realiza de forma similar al comando `System, RefreshAllScripts` con la excepción de que solo se actualizan los archivos especificados. Esto puede ahorrar tiempo si no necesita actualizar todo el árbol del proyecto, que podría abarcar varios proyectos y docenas de secuencias de comandos.

El script especificado debe existir actualmente en el árbol del proyecto o la operación fallará. Si necesita cargar un nuevo script en el proyecto, use el comando `LoadNewScript` en su lugar.

Debido a una limitación del sistema, PEBakery no puede actualizar el script actual `% ScriptFile%` durante la compilación de un proyecto. El comando se verá afectado después de que finalice la construcción actual.

Cuando se usan comodines, todos los directorios bajo `FilePath` se escanean para el patrón especificado. Use el indicador `NOREC` para deshabilitar este comportamiento.

## Relacionado

[System,LoadNewScript.md](./LoadNewScript.md), [System,RefreshAllScripts.md](./RefreshAllScripts.md)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=RefreshScript Ejemplo
Author=Homes32
Description=Demostrar el uso del comando system,RefreshScript.
Version=1
Level=5

[Interface]
BTN_Load=Refresh,1,8,15,60,80,25,Process,0,False,_Process_,False
BTN_Clean=Cleanup,1,8,100,60,80,25,Clean,0,True,_Clean_,True

[variables]
%myScript%=%ProjectDir%\myScript.script

[Clean]
Echo,"Removiendo myScript Examplo..."
If,EXISTFILE,%myScript%,FileDelete,%myScript%
System,RefreshAllScripts

[process]
If,Not,ExistFile,%myScript%,FileCreateBlank,%myScript%

// Crear un nuevo Script
IniWrite,%myScript%,Main,Title,myScript
IniWrite,%myScript%,Main,Author,Homes32
IniWrite,%myScript%,Main,Description,"A brand new Script!"
IniWrite,%myScript%,Main,Version,1
IniWrite,%myScript%,Main,Level,5
IniWrite,%myScript%,Main,Selected,False

// cargarlo en nuestro proyecto
System,LoadNewScript,%myScript%,Extra

// Hacer algunas modificaciones a nuestro script
TXTAddLine,%myScript%,"[Variables]",Append
TXTAddLine,%myScript%,"",Append
TXTAddLine,%myScript%,"[Process]",Append
TXTAddLine,%myScript%,"[Interface]",Append
TXTAddLine,%myScript%,"",Append

// actualizar el script para que nuestras modificaciones tengan efecto
Echo,"Refreshing %myScript%..."
System,RefreshScript,%myScript%
```
