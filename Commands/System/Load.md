# System,Load

Escanea la ruta especificada para proyectos y scripts nuevos/modificados y los agrega al árbol del proyecto.

## Sintaxis

```pebakery
System,Load,<FilePath>,[NOREC]
```

### Argumentos

| Argumento | Descripción |
| --- | --- |
| FilePath | La ruta al archivo de script para cargar. Los comodines (*?) son compatibles y se pueden usar para escanear multiples archivos. |

### Flags (Indicadores)

| Flag | Descripción |
| --- | --- |
| NOREC | **(Opcional)** No recursivo a subdirectorios. - Cuando se utilizan comodines, se escanean todos los directorios bajo `FilePath`. Use esta flag (indicador) para desactivar este comportamiento. |

## Observaciones

Este comando se puede utilizar para reconstruir el árbol del proyecto cuando se agrega o modifica un script y se realiza de forma similar al comando `System,LoadAll` con la excepción de que solo se cargan los archivos especificados. Esto puede ahorrar tiempo si no necesita actualizar todo el árbol del proyecto, que podría abarcar varios proyectos y docenas de scripts.

Debido a una limitación del sistema, PEBakery no puede `Cargar` el script actual `%ScriptFile%` durante la compilación de un proyecto. El comando tendrá afecto después de que finalice la construcción actual.

## Relacionado

[System,LoadAll](./LoadAll.md)

## Ejemplos

### Ejemplo 1

```pebakery
[Main]
Title=Load Ejemplo
Author=Homes32
Description=Mostrar el uso del comando System,Load.
Version=1
Level=5

[Interface]
CB_Recurse="Scan inside subdirectories",1,3,15,30,200,20,True
BTN_Load=Load,1,8,15,60,80,25,Process,0,False,_Process_,False
BTN_Clean=Cleanup,1,8,100,60,80,25,Clean,0,True,_Clean_,True

[variables]
%myProject%=%BaseDir%\Projects\myProject\script.project
%myScript%=%BaseDir%\Projects\myProject\myScript.script
%mySubDir%=%BaseDir%\Projects\myProject\SubDir\folder.project
%myScript2%=%BaseDir%\Projects\myProject\SubDir\myScript2.script

[Clean]
Echo,"Remover myProject Ejemplo..."
If,EXISTDIR,%BaseDir%\Projects\myProject\,DirDelete,%BaseDir%\Projects\myProject\
System,LoadAll

[process]

If,Not,ExistFile,%myProject%,FileCreateBlank,%myProject%
If,Not,ExistFile,%myScript%,FileCreateBlank,%myScript%

// Proyecto
IniWrite,%myProject%,Main,Title,myProject
IniWrite,%myProject%,Main,Author,Homes32
IniWrite,%myProject%,Main,Description,"¡Un nuevo proyecto!"
IniWrite,%myProject%,Main,Version,1
IniWrite,%myProject%,Main,Level,5

TXTAddLine,%myProject%,"[Variables]",Append
TXTAddLine,%myProject%,"",Append
TXTAddLine,%myProject%,"[Process]",Append
TXTAddLine,%myProject%,"[Interface]",Append
TXTAddLine,%myProject%,"",Append

// Script
IniWrite,%myScript%,Main,Title,myScript
IniWrite,%myScript%,Main,Author,Homes32
IniWrite,%myScript%,Main,Description,"¡Un nuevo script!"
IniWrite,%myScript%,Main,Version,1
IniWrite,%myScript%,Main,Level,5
IniWrite,%myScript%,Main,Selected,False

TXTAddLine,%myScript%,"[Variables]",Append
TXTAddLine,%myScript%,"",Append
TXTAddLine,%myScript%,"[Process]",Append
TXTAddLine,%myScript%,"[Interface]",Append
TXTAddLine,%myScript%,"",Append

// Subdirectorio de Scripts
//IniWrite,%mySubDir%,Main,Title,myApps
//IniWrite,%mySubDir%,Main,Author,Homes32
//IniWrite,%mySubDir%,Main,Description,"Una carpeta para myApps"
//IniWrite,%mySubDir%,Main,Version,1

// Scripts en Subdirectorio
IniWrite,%myScript2%,Main,Title,myScript2
IniWrite,%myScript2%,Main,Author,Homes32
IniWrite,%myScript2%,Main,Description,"¡Un nuevo script en un subdirectorio!"
IniWrite,%myScript2%,Main,Version,1
IniWrite,%myScript2%,Main,Level,5
IniWrite,%myScript2%,Main,Selected,False

TXTAddLine,%myScript2%,"[Variables]",Append
TXTAddLine,%myScript2%,"",Append
TXTAddLine,%myScript2%,"[Process]",Append
TXTAddLine,%myScript2%,"[Interface]",Append
TXTAddLine,%myScript2%,"",Append

// Ahora necesitamos llamar al siguiente comando para que nuestro nuevo proyecto y script se muestren en la ventana principal.
If,%CB_Recurse%,Equal,True,Begin
  // Escanee los siguientes directorios y todos los subdirectorios.
  Echo,"Cargando todos los scripts bajo %BaseDir%\Proyectos\miProyecto\"
  System,Load,%BaseDir%\Projects\myProject\*.*
End
Else,Begin
  // No escanear subdirectorios
  Echo,"Cargando solo scripts ubicados en %BaseDir%\Proyectos\miProyecto\directorios."
  System,Load,%BaseDir%\Projects\myProject\*.*,NOREC
End
```
